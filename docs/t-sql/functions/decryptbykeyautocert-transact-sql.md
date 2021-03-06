---
title: DECRYPTBYKEYAUTOCERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/09/2015
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECRYPTBYKEYAUTOCERT
- DECRYPTBYKEYAUTOCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DECRYPTBYKEYAUTOCERT function
ms.assetid: 6b45fa2e-ffaa-46f7-86ff-5624596eda4a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3bf53e51d3896953e66e3360aaa810a5c13c51ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="decryptbykeyautocert-transact-sql"></a>DECRYPTBYKEYAUTOCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  証明書で自動的に暗号化解除された対称キーを使用し、暗号化を解除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DecryptByKeyAutoCert ( cert_ID , cert_password   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }   
  [ , { authenticator | @authenticator } ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *cert_ID*  
 対称キーの保護に使用されている証明書の ID です。 *Cert_ID* は **int**です。  
  
 *cert_password*  
 証明書の秘密キーを保護するパスワードを指定します。 秘密キーがデータベースのマスター キーで保護されている場合は NULL を指定できます。 *cert_password* は **nvarchar**です。  
  
 '*ciphertext*'  
 キーで暗号化されたデータです。 *暗号化テキスト* は **varbinary**です。  
  
 @ciphertext  
 キーを使用して暗号化されたデータを含む **varbinary** 型の変数を指定します。  
  
 *add_authenticator*  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 データを暗号化するときに EncryptByKey に渡されたものと同じ値である必要があります。 **1** 認証子が使用された場合。 *add_authenticator* は **int**です。  
  
 @add_authenticator  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 データを暗号化する際に EncryptByKey に渡された値と同じである必要があります。  
  
 *authenticator*  
 認証子の生成元のデータを指定します。 EncryptByKey に渡された値と一致する必要があります。 *認証システム* は **sysname**です。  
  
 @authenticator  
 認証子の生成元のデータを含む変数を指定します。 EncryptByKey に渡された値と一致する必要があります。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>Remarks  
 DecryptByKeyAutoCert は、OPEN SYMMETRIC KEY および DecryptByKey の機能を組み合わせたもので、 対称キーの暗号化解除と、そのキーを使用した暗号化テキストの暗号化解除を 1 回の操作で行います。  
  
## <a name="permissions"></a>アクセス許可  
 対称キーに対する VIEW DEFINITION 権限と、証明書に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`DecryptByKeyAutoCert` を使用して暗号化解除の実行コードを簡素化する方法を示します。 このコードは、データベース マスター キーが存在しない [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで実行する必要があります。  
  
```  
--Create the keys and certificate.  
USE AdventureWorks2012;  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
OPEN MASTER KEY DECRYPTION BY PASSWORD = 'mzkvdlk979438teag$$ds987yghn)(*&4fdg^';  
CREATE CERTIFICATE HumanResources037   
   WITH SUBJECT = 'Sammamish HR',   
   EXPIRY_DATE = '10/31/2009';  
CREATE SYMMETRIC KEY SSN_Key_01 WITH ALGORITHM = DES  
    ENCRYPTION BY CERTIFICATE HumanResources037;  
GO  
----Add a column of encrypted data.  
ALTER TABLE HumanResources.Employee  
    ADD EncryptedNationalIDNumber varbinary(128);   
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037 ;  
UPDATE HumanResources.Employee  
SET EncryptedNationalIDNumber  
    = EncryptByKey(Key_GUID('SSN_Key_01'), NationalIDNumber);  
GO  
--  
--Close the key used to encrypt the data.  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--There are two ways to decrypt the stored data.  
--  
--OPTION ONE, using DecryptByKey()  
--1. Open the symmetric key  
--2. Decrypt the data  
--3. Close the symmetric key  
OPEN SYMMETRIC KEY SSN_Key_01  
   DECRYPTION BY CERTIFICATE HumanResources037;  
SELECT NationalIDNumber, EncryptedNationalIDNumber    
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKey(EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
CLOSE SYMMETRIC KEY SSN_Key_01;  
--  
--OPTION TWO, using DecryptByKeyAutoCert()  
SELECT NationalIDNumber, EncryptedNationalIDNumber   
    AS 'Encrypted ID Number',  
    CONVERT(nvarchar, DecryptByKeyAutoCert ( cert_ID('HumanResources037') , NULL ,EncryptedNationalIDNumber))   
    AS 'Decrypted ID Number'  
    FROM HumanResources.Employee;  
```  
  
## <a name="see-also"></a>参照  
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbykey-transact-sql.md)   
 [DECRYPTBYKEY &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbykey-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
