---
title: 詳細グループの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b8c504724523a3e331a54137766504b3599587c2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33019759"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>詳細グループの追加 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートでは、レポート データセットの詳細データは、グループ式のないグループとして指定されます。 マトリックスの詳細データを表示したり、表や一覧から削除した詳細データを再び追加したり、詳細グループを追加したりするときは、既存の Tablix データ領域に詳細グループを追加します。 グループの詳細については、「 [グループについて (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-details-group-to-a-tablix-data-region"></a>詳細グループを Tablix データ領域に追加するには  
  
1.  デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。 グループ化ペインに、選択したデータ領域の行グループと列グループが表示されます。  
  
2.  [グループ化] ペインで、最も内側の子グループを右クリックします。 **[グループの追加]** をクリックし、 **[子グループ]** をクリックします。 **[Tablix のグループ]** ダイアログ ボックスが表示されます。  
  
3.  **[グループ式]** で式を空白のままにします。 詳細グループには式がありません。  
  
4.  **[詳細データの表示]** をクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     グループ化ペインで新しい詳細グループが子グループとして追加され、手順 1. で選択したグループの行ハンドルに詳細グループ アイコンが表示されます。 Tablix データ領域に関する詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ領域でのグループの追加または削除 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [グループについて &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)   
 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [テーブル &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) [マトリックス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)      
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
