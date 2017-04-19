---
title: "SQL Server の証明書と非対称キー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [SQL Server], 証明書と非対称キー"
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# SQL Server の証明書と非対称キー
  公開キー暗号化 (PKI) は、メッセージを秘匿する方法の 1 つです。この方法では、ユーザーが*公開*キーと*秘密*キーを作成します。 秘密キーは秘匿されますが、公開キーは他のユーザーに配布できます。 2 つのキーは数学的に相関していますが、公開キーを使用して秘密キーを簡単に導出することはできません。 公開キーはデータの暗号化に使用され、秘密キーはデータの暗号化解除に使用されます。 公開キーを使用して暗号化されたメッセージは、正しい秘密キーを使用しないと暗号化解除できません。 2 つの異なるキーが存在するので、これらのキーは*非対称*です。  
  
 証明書と非対称キーは、どちらも非対称暗号化を使用するための手段です。 証明書は、有効期限や発行者などの詳細情報を格納できることから、非対称キーのコンテナーとしてよく使用されます。 この 2 つのメカニズムに暗号化アルゴリズムの違いはなく、同じキー長が指定された場合の強度にも違いはありません。 一般に、データベース内の他の種類の暗号化キーを暗号化する場合や、コード モジュールに署名する場合は、証明書を使用します。  
  
 証明書と非対称キーは、一方が暗号化したデータを暗号化解除できます。 一般に、データベース内のストレージに対する対称キーを暗号化する場合は、非対称暗号化を使用します。  
  
 公開キーには証明書のような特定の形式がありません。また、公開キーはファイルにエクスポートできません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、サーバーとデータベースで使用するための証明書とキーを作成および管理できる機能が用意されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、他のアプリケーションやオペレーティング システム用の証明書とキーを作成および管理することはできません。  
  
## 証明書  
 証明書は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の公開キー (およびオプションで秘密キー) を含んでいるデジタル署名されたセキュリティ オブジェクトです。 外部で生成された証明書を使用するか、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で証明書を生成できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 証明書は、IETF X.509v3 の証明書標準に準拠しています。  
  
 証明書は、X.509 証明書ファイルに対してキーをエクスポートおよびインポートできるので便利です。 証明書を作成する構文では、有効期限などの証明書の作成オプションを指定できます。  
  
### SQL Server での証明書の使用  
 証明書は、データベース ミラーリングで接続を保護したり、パッケージや他のオブジェクトに署名したり、データや接続を暗号化したりする場合に使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の証明書に関するその他のリソースを次の表に示します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)|証明書を作成するためのコマンドについて説明します。|  
|[デジタル署名を使用してパッケージのソースを特定する](../../integration-services/packages/identify-the-source-of-packages-with-digital-signatures.md)|証明書を使用してソフトウェア パッケージに署名する方法について説明します。|  
|[データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|データベース ミラーリングで証明書を使用する方法について説明します。|  
  
## 非対称キー  
 非対称キーは、対称キーを保護するために使用します。 また、制限付きでデータを暗号化する場合や、データベース オブジェクトにデジタル署名する場合にも使用できます。 非対称キーは、秘密キーと対応する公開キーで構成されます。 非対称キーの詳細については、「[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)」を参照してください。  
  
 非対称キーは、厳密な名前のキー ファイルからインポートできますが、エクスポートすることはできません。 また、有効期限のオプションもありません。 非対称キーで接続を暗号化することはできません。  
  
### SQL Server での非対称キーの使用  
 非対称キーは、データを保護したり、プレーンテキストに署名したりする場合に使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での非対称キーに関するその他のリソースを次の表に示します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)|非対称キーを作成するためのコマンドについて説明します。|  
|[SIGNBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/signbyasymkey-transact-sql.md)|オブジェクトに署名するためのオプションについて説明します。|  
  
## ツール  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、証明書および厳密な名前のキー ファイルを生成するツールとユーティリティを提供しています。 これらのツールでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構文よりも柔軟にキーを生成できます。 これらのツールを使用することで、より複雑なキー長の RSA キーを作成して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にインポートできます。 次の表では、これらのツールの入手先を示します。  
  
|||  
|-|-|  
|ツール|用途|  
|[makecert](http://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|証明書を作成します。|  
|[sn](http://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|対称キーの厳密名を作成します。|  
  
## 関連タスク  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
  
## 参照  
 [sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)   
 [透過的なデータ暗号化 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
  
  