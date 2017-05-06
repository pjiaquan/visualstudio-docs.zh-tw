---
title: "如何：匯入主版頁面或佈景主題"
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
  - "匯入項目 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 匯入項目"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：匯入主版頁面或佈景主題
  您可以建立和使用主版頁面和佈景主題，讓 SharePoint 網站中的網頁具有一致的外觀。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不會提供這些項目的範本，但您可以在 SharePoint Designer 中，然後將其匯入 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  如需詳細資訊，請參閱 Microsoft 網站上的 [建置組塊：頁面和使用者介面](http://go.microsoft.com/fwlink/?LinkID=182095)。  
  
### 若要匯入主版頁面或佈景主題  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立或開啟 SharePoint 專案。  
  
     如需如何建立 SharePoint 專案的詳細資訊，請參閱 [SharePoint 專案與專案項目範本](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  在\[ **加入新項目**\]對話方框中展開**SharePoint**節點，接著選取**2010**節點  
  
4.  在 SharePoint 範本清單中，選取 \[**模組**\] 範本，然後為模組指定名稱。  
  
     模組包含檔案 \(如主版頁面或佈景主題檔案\)，以便將檔案部署到 SharePoint 中的指定位置。  
  
5.  在模組中，刪除預設命名為 Sample.txt 的檔案。  
  
6.  選擇模組節點。  
  
7.  在功能表列上，選擇 \[**專案**\]， \[**加入現有項目**\]，然後選取主版頁面或佈景主題檔案。  
  
     主版頁面檔案的副檔名為 .master，而佈景主題檔案的副檔名為 .thmx。  
  
8.  如果您已加入主版頁面，將其 \[**部署衝突解決**\] 設定變更為模組屬性的 \[**自動**\]。  
  
    > [!NOTE]  
    >  如果主版頁面的名稱與標示為「預設主版頁面」或「自訂主版頁面」的現有主版頁面名稱相同，則會發生錯誤。  如需如何解決此問題的詳細資訊，請參閱[逐步解說：匯入自訂主版頁面及包含影像的網站頁面](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)。  
  
9. 在模組中，開啟 Elements.xml。  
  
     您必須更新 Elements.xml 檔案來參考您所加入的主版頁面或佈景主題。  
  
10. 如果是主版頁面，請使用下列標記取代現有的模組標記。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     如果是佈景主題，請使用下列標記取代現有的模組標記。  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     請務必使用模組和主版頁面或佈景主題的實際名稱來取代預留位置值。  
  
     `Type="GhostableInLibrary"` 屬性表示此項目加入至內容資料庫，而且模組的 `Url` 屬性會指定要將檔案儲存在 SharePoint 內容資料庫中的哪一個位置。  
  
11. 若要變更主版頁面的部署範圍，請在 \[**方案總管**\] 中，開啟功能設計工具中的功能檔案，從 \[**範圍**\] 清單中選擇新的部署範圍。  
  
     \[**Web**\] 值表示主版頁面只會套用到目前在專案中指定的網站。  \[**網站**\] 值表示主版頁面會套用到目前的網站集合，其中包括所有子網站和根網站。  其他的值則不適用。  
  
    > [!NOTE]  
    >  因為佈景主題只適用於網站集合層級，所以我們建議您不要將佈景主題的範圍設定為 \[**網站**\] 以外的任何值。  如果在子網站中使用佈景主題，可能會發生錯誤。  
  
12. 在功能表列上，選擇 \[**建置**\]、\[**部署方案**\]。  
  
13. 若要驗證檔案是否正確部署，開啟 SharePoint 網站，選取 \[**網站動作**\] 功能表上，選擇 \[**網站設定**\] 命令，然後選擇 \[**主版頁面**\] 連結或 \[**佈景主題**\] 連結。  
  
     主版頁面或佈景主題清單隨即出現並包含您要匯入的主版頁面或佈景主題。  
  
## 請參閱  
 [主版頁面](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [建立 SharePoint 的網頁](../sharepoint/creating-pages-for-sharepoint.md)   
 [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  