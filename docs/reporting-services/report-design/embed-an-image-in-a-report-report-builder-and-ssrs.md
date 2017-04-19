---
title: "レポートへの画像の埋め込み (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rtp.rptdesigner.embeddedimages.f1"
  - "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# レポートへの画像の埋め込み (レポート ビルダーおよび SSRS)
  レポートには、画像を埋め込むことができます。 画像の埋め込みには、レポートの画像を常に利用可能な状態にできるというメリットはありますが、レポート定義 (レポートを定義するファイル) のサイズは大きくなる可能性があります。 レポートに埋め込まれた画像は、レポート データ ペインに一覧表示されます。  
  
 デザイン画面に画像を追加する前にレポート定義に画像を埋め込むことができます。 詳細については、「[背景画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### レポートに画像を埋め込むには  
  
1.  レポート デザイン ビューの **[挿入]** タブで、**[画像]** をクリックします。  
  
2.  デザイン画面で、ボックスをクリックし、画像の目的のサイズにドラッグします。  
  
3.  **[画像のプロパティ]** ダイアログ ボックスの **[全般]** ページにある **[名前]** ボックスに名前を入力するか、既定値を受け入れます。  
  
4.  (省略化) **[ツールヒント]** ボックスで、ユーザーが表示レポートの画像の上にマウスを置いたときに表示されるテキストを入力します。  
  
5.  **[画像ソースの選択]** で、**[埋め込み]** を選択します。  
  
6.  **[次の画像を使用]** ボックスの横にある **[インポート]** ボタンをクリックします。  
  
7.  **[ファイルの種類]** で画像ファイルの種類を選択し、ファイルに移動し、**[開く]** をクリックします。  
  
8.  **[画像のプロパティ]** ダイアログ ボックスで、**[OK]** をクリックします。  
  
     デザイン画面に描画したボックス内に画像が表示され、レポート データ ペインの [画像] フォルダー内にファイルが表示されます。  
  
    > [!NOTE]  
    >  また、MIME の種類 (例 : bmp) は、画像がインポートされるときに自動的に取得されます。 MIME の種類を変更するには、次の手順を参照してください。  
  
### (省略可) インポートされた画像の MIME の種類を変更するには  
  
1.  [デザイン] ビューでレポートを開きます。  
  
2.  デザイン画面で画像を選択します。 **プロパティ** ペインに画像のプロパティが表示されます。  
  
    > [!NOTE]  
    >  プロパティ ペインが表示されていない場合は、**[表示]** タブの **[プロパティ]** をクリックします。  
  
3.  **[MIMEType]** プロパティの横にあるボックス内をクリックし、ボックスの一覧から新しい MIME の種類を選択します。  
  
## 参照  
 [画像 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [データバインド画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-data-bound-image-report-builder-and-ssrs.md)   
 [[画像のプロパティ] ダイアログ ボックス &#40;レポート ビルダーおよび SSRS&#41;](../Topic/Image%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  