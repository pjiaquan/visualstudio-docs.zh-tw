---
title: "如何：新增與移除對應的資料夾"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "對應資料夾 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 對應資料夾"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：新增與移除對應的資料夾
  SharePoint 中部分常用的資料夾 \(如「影像」和「配置」\) 會內嵌在檔案階層的底層。  您可以將這些資料夾對應至 SharePoint 專案中，以便更容易存取它們。  對應資料夾是 SharePoint 專案中與 SharePoint 伺服器安裝中檔案實體位置對應的資料夾。  
  
 當您部署 SharePoint 應用程式時，方案套件 \(.wsp\) 會將對應資料夾及其所有資料夾的內容複製到在跑 SharePoint 伺服器上 SharePoint 資料夾樹的指定位置。  此位置是由針對對應資料夾設定的 **Deployment Location** 屬性所決定。  對應資料夾中的任何子資料夾都相對於對應資料夾的 **Deployment Location**。  請注意，對應資料夾的名稱並不會決定部署項目的位置，而是由 **Deployment Location** 屬性決定。  
  
 您可以使用選單或是捷徑功能表上的命令，將對應資料夾加入至專案。  您可以使用 \[**加入 SharePoint image 對應資料夾**\] 和 \[**加入 SharePoint 「配置」資料夾**\] 命令加入最常用的對應資料夾。  您可以將其他可用的 SharePoint 資料夾中的任一個加入至您的專案使用 \[**加入 SharePoint 對應資料夾**\] 命令在捷徑功能表中指定資料夾在 \[**加入 SharePoint 對應資料夾**\] 對話方塊。  
  
## 將對應資料夾加入至專案  
 下列程序說明如何將兩個對應資料夾加入視覺物件網頁組件專案。  若要開始，您可以建立視覺 Web 組件專案。  
  
#### 若要將對應資料夾加入至專案  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中的 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**Office\/SharePoint**\]節點，然後選擇 \[**SharePoint 方案**\] 節點。  
  
3.  在專案範本清單中，選取 \[**SharePoint 2013 視覺 Web 組件**\] 範本。  
  
4.  在 \[**名稱**\] 方塊中，輸入 **TestProject1**，然後選擇 \[確定\] 按鈕。  
  
5.  在 \[**SharePoint 自訂精靈**\] 中，選取 \[**結束**\] 按鈕保留預設值。  
  
6.  在 \[**方案總管**\] 中，選擇專案節點，然後在功能表列上選擇 \[ **專案**\]、\[**加入 SharePoint "圖片" 對應子夾**\]。  
  
     名為 \[**影像**\] 的資料夾會出現在您的專案會包含名為 TestProject1 的子資料夾。  這個對應資料夾將包含視覺 Web 組件專案的影像。  
  
7.  選擇 \[**方案總管**\] 中的專案節點，然後在選單條中指向 \[**加入**\]，再加入 \[**SharePoint 對應資料夾**\] 以顯示 \[**加入 SharePoint 對應資料夾**\] 對話方塊。  
  
8.  在提供將可用的資料夾的樹狀檢視中，選取 \[**資源**\] 資料夾，然後選擇 \[**好**\] 按鈕。  
  
     名為 \[**資源**\] 的資料夾會出現在您的專案。  它可以儲存類似字串資源檔的項目。  子資料夾對於組織對應資料夾的內容很有幫助，但是當您使用 \[**加入 SharePoint 對應資料夾**\] 命令加入對應資料夾時，並不會自動建立子資料夾。  若要加入子資料夾，請選取 \[**資源**\] 資料夾，然後，在功能表列上，選擇 \[**專案**\]，則 \[**新的資料夾**\]。  
  
## 變更對應資料夾的部署位置  
 根據預設，對應資料夾會加入特定位置至 SharePoint 根安裝 \(以語彙基元 {SharePointRoot} 表示\) 的相對位置。  不過，您可以變更對應資料夾的 **Deployment location** 屬性來變更此位置。  每個對應資料夾都有專屬的 **Deployment location** 屬性。  
  
#### 若要變更對應資料夾的部署位置  
  
1.  在先前建立的專案中，選擇對應資料夾。  
  
2.  在 \[**屬性**\] 視窗中，選擇 **Deployment location** 屬性的省略符號按鈕 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\)。  
  
3.  在 \[**加入 SharePoint 對應資料夾**\] 對話方塊中，瀏覽至您要對應資料夾指向的資料夾。  
  
4.  選擇節點，然後選擇 \[**確定**\] 按鈕。  
  
## 重新命名或移除對應資料夾  
  
#### 若要重新命名或移除對應資料夾  
  
1.  在先前建立的專案中，選擇對應資料夾。  
  
2.  若要重新命名對應資料夾，請選取捷徑功能表上的 \[**重新命名**\]，然後輸入新名稱，再選擇 Enter。  
  
     或者，您可以選取要重新命名的對應資料夾，開啟 \[**屬性**\] 視窗，然後將 **Folder name** 屬性的值設定為新的名稱。  
  
3.  若要移除專案中的對應資料夾，請選取捷徑功能表上的 \[**刪除**\]，然後選擇對話方塊中的 \[**確定**\] 按鈕確認移除。  
  
## 請參閱  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  