---
title: "逐步解說：設計 Outlook 表單區域"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "表單區域 [Visual Studio 中的 Office 程式開發], 建立"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 逐步解說：設計 Outlook 表單區域
  自訂的表單區域會擴充標準或自訂的 Microsoft Office Outlook 表單。  在此逐步解說中，您要設計自訂的表單區域，它在連絡人項目的 \[偵測器\] 視窗中會顯示為新頁面。  這個表單區域會將地址資訊傳送至 Windows Live 當地搜尋網站，顯示連絡人清單中每個地址的對應。  如需表單區域的相關資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立新的 Outlook VSTO 增益集專案。  
  
-   在 VSTO 增益集專案中加入表單區域。  
  
-   設計表單區域的版面配置。  
  
-   自訂表單區域的行為。  
  
-   測試 Outlook 表單區域。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 或 [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]。  
  
 ![視訊的連結](~/docs/data-tools/media/playvideo.gif "視訊的連結") 如需本主題的影片版本，請參閱[影片 \- 如何：設計 Outlook 表單區域](http://go.microsoft.com/fwlink/?LinkID=140824)。  
  
## 建立新的 Outlook VSTO 增益集專案  
 第一次建立基本的 VSTO 增益集專案。  
  
#### 建立新的 Outlook VSTO 增益集專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，建立名為 MapItAddIn 的 Outlook VSTO 增益集專案。  
  
2.  在 \[新增專案\] 對話方塊中，選取 \[為方案建立目錄\]。  
  
3.  將專案儲存至任一目錄。  
  
     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
## 在 Outlook VSTO 增益集專案中加入表單區域  
 Outlook VSTO 增益集解決方案可以包含一或多個 Outlook 表單區域項目。  使用 \[新的 Outlook 表單區域精靈\] 將表單區域項目加入專案。  
  
#### 在 Outlook VSTO 增益集專案中加入表單區域  
  
1.  在 \[方案總管\] 中，選取 \[MapItAddIn\] 專案。  
  
2.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
3.  在 \[加入新項目\] 對話方塊中，選取 \[Outlook 表單區域\]，將檔案命名為 MapIt，然後按一下 \[加入\]。  
  
     如此會啟動 \[新的 Outlook 表單區域精靈\]。  
  
4.  在 \[選取您希望如何建立此表單區域\] 頁面上，按一下 \[設計新的表單區域\]，然後按一下 \[下一步\]。  
  
5.  在 \[選取要建立的表單區域類型\] 頁面上，按一下 \[個別\]，然後按一下 \[下一步\]。  
  
     *「個別」*\(separate\) 表單區域會在 Outlook 表單中加入新的頁面。  如需表單區域型別的詳細資訊，請參閱[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
6.  在 \[提供描述文字和選取顯示設定\] 頁面的 \[名稱\] 方塊中，輸入 **Map It**。  
  
     開啟連絡人項目時，這個名稱會出現在 \[偵測器\] 視窗的功能區上。  
  
7.  選取 \[處於撰寫模式的偵測器\] 和 \[處於讀取模式的偵測器\]，然後按一下 \[下一步\]。  
  
8.  在 \[識別將顯示此表單區域的訊息類別\] 頁面上，清除 \[郵件\] 並選取 \[連絡人\]，然後按一下 \[完成\]。  
  
     MapIt.cs 或 MapIt.vb 檔案即會加入專案。  
  
## 設計表單區域的版面配置  
 使用*「表單區域設計工具」*\(form region designer\) 以視覺化方式開發表單區域。  您可以將 Managed 控制項拖曳至表單區域設計工具介面。  請使用設計工具和 \[屬性\] 視窗調整控制項的版面配置和外觀。  
  
#### 設計表單區域的版面配置  
  
1.  在 \[方案總管\] 中展開 \[MapItAddIn\]專案，然後再連按兩下 MapIt.cs 或 MapIt.vb 開啟表單區域設計工具。  
  
2.  以滑鼠右鍵按一下設計工具，再按一下 \[屬性\]。  
  
3.  在 \[屬性\] 視窗中，將 \[大小\] 設為 664、469。  
  
     這可確保表單區域大到足以顯示地圖。  
  
4.  在 \[**檢視**\] 功能表上，按一下 \[**工具箱**\]。  
  
5.  從 \[工具箱\] 的 \[通用控制項\] 索引標籤，將 \[Web 瀏覽器\] 加入表單區域。  
  
     \[Web 瀏覽器\] 會顯示連絡人清單中每個地址的對應。  
  
## 自訂表單區域的行為  
 在表單區域事件處理常式中加入程式碼，以自訂表單區域在執行階段的行為方式。  程式碼會檢查此表單區域的 Outlook 項目屬性，並決定是否要顯示 Map It 表單區域。  如果它顯示表單區域，程式碼會瀏覽至 Windows Live 當地搜尋，並載入 Outlook 連絡人項目中所列的每個地址的對應。  
  
#### 自訂表單區域的行為  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下 MapIt.cs 或 MapIt.vb，再按一下 \[檢視程式碼\]。  
  
     MapIt.cs 或 MapIt.vb 會在程式碼編輯器中開啟。  
  
2.  展開 \[表單區域 Factory\] 程式碼區域。  
  
     即會公開名為 `MapItFactory` 的表單區域 Factory 類別。  
  
3.  將下列程式碼加入至 `MapItFactory_FormRegionInitializing` 事件處理常式。  當使用者開啟連絡人項目時，即會呼叫這個事件處理常式。  下列程式碼會判斷連絡人項目是否包含地址。  如果連絡人項目不包含地址，這個程式碼就會將 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 類別的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性設成 **true**，且不顯示表單區域。  否則，VSTO 增益集會引發 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件，並顯示表單區域。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  將下列程式碼加入至 <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> 事件處理常式。  這個程式碼會執行下列工作：  
  
    -   串連連絡人項目中的每個地址，並建立 URL 字串。  
  
    -   呼叫 <xref:System.Windows.Forms.WebBrowser> 物件的<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法，並將 URL 字串當成參數傳遞。  
  
     當地搜尋網站會出現在 Map It 表單區域中，並在便條簿中顯示每個地址。  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## 測試 Outlook 表單區域  
 當您執行專案時，Visual Studio 會開啟 Outlook。  開啟連絡人項目，以檢視 Map It 表單區域。  在包含地址的任何連絡人項目表單中，Map It 表單區域會顯示為頁面。  
  
#### 測試 Map It 表單區域  
  
1.  按 F5 執行專案。  
  
     Outlook 即開啟。  
  
2.  在 Outlook 的 \[住家\] 索引標籤上，按一下 \[新增項目\]，然後按一下 \[連絡人\]。  
  
3.  在連絡人表單中，輸入連絡人名稱**王美美**，然後指定下列三個地址。  
  
    |地址類型|地址|  
    |----------|--------|  
    |**商務**|民權東路 4567 號  台北市|  
    |**首頁**|中山北路 1234 號  台北市|  
    |**其他**|自由路 5796 號  台中市|  
  
4.  儲存並關閉連絡人項目。  
  
5.  重新開啟 \[王美美\] 連絡人項目。  
  
6.  在項目功能區的 \[顯示\] 群組中，按一下 \[Map It\] 開啟 Map It 表單區域。  
  
     Map It 表單區域即出現並顯示當地搜尋網站。  便條簿中即會出現 \[商務\]、\[住家\] 和 \[其他\] 位址。  在便條簿中選取想要對應的地址。  
  
## 後續步驟  
 從這些主題，您可以進一步了解如何自訂 Outlook 應用程式的 UI：  
  
-   若要深入了解如何自訂 Outlook 項目的功能區，請參閱[自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)。  
  
## 請參閱  
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [建立 Outlook 表單區域的方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [讓表單區域與 Outlook 訊息類別產生關聯](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Outlook 表單區域中的自訂動作](../vsto/custom-actions-in-outlook-form-regions.md)   
 [如何：防止 Outlook 顯示表單區域](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  