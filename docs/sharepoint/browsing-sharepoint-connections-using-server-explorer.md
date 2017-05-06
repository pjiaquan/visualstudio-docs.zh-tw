---
title: "使用伺服器總管瀏覽 SharePoint 連線"
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
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint 連接 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 瀏覽 SharePoint 網站"
  - "Visual Studio 中的 SharePoint 開發, SharePoint 連接"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 使用伺服器總管瀏覽 SharePoint 連線
  您現在可以在 \[**伺服器總管**\] 瀏覽本機 SharePoint 連接。  透過使用這項技術，您可以巡覽位於系統中 SharePoint 網站的元件。  SharePoint 網站元件 \(例如清單定義和內容類型\) 會出現在 \[**伺服器總管**\] 樹狀檢視中名為 \[**SharePoint 連接**\] 的節點。  若要顯示 \[**伺服器總管**\]，請在功能表上選擇 \[**檢視**\]、\[**伺服器總管**\]。  除了顯示 SharePoint 網站元件，您可以使用捷徑功能表的命令，來移除項目、檢視其屬性或重新整理樹狀檢視。  
  
> [!IMPORTANT]  
>  若要瀏覽 SharePoint 網站，您必須是 SharePoint 網站集合上的系統管理員，也必須以本機電腦 Administrator 使用者身分來執行 Visual Studio。  否則，網站會出現在 \[**伺服器總管**\] 中，但您無法展開其節點。  若要確認您是否為網站集合的系統管理員，在瀏覽器中開啟網站，開啟 \[**網站動作**\] 功能表，選取 \[**網站的使用權限**\]，然後，在 \[**使用權限:小組網站**\] 頁面上，從功能區的 \[**處理**\] 群組中，選擇 \[**網站集合管理員**\] 命令。  如果您是網站集合管理員，您的名稱將會出現在文字方塊中。  如果 \[**網站集合管理員**\] 命令無法在功能區上的管理群組中出現，代表您不是網站集合的系統管理員，因此您必須從網站管理員取得適當權限。  
  
## 伺服器總管節點  
 SharePoint 網站的每個元件都會以 \[**伺服器總管**\] 樹狀檢視中、\[**SharePoint 連接**\] 底下的節點表示。  例如，預設 SharePoint 網站包含名為「討論區」的內容類型，這代表會顯示在 SharePoint 網站的 \[**討論區**\] 頁面的討論區類型。  「討論區」內容類型包含數個欄位。  若要在 \[**SharePoint 總管**\] 中檢視這些欄位，請展開 \[**內容類型**\] 節點，然後展開 \[**討論區**\] 節點。  在它底下有數個欄位節點，例如 \[本文\]、\[討論主題\] 和 \[標題\]。  
  
## 節點捷徑功能表命令  
 每個節點可以滑鼠右鍵按一下節點或選取它，然後選取 Shift\+F10 索引鍵來存取捷徑功能表。  節點命令可能包括下列各項：  
  
|命令名稱|說明|  
|----------|--------|  
|重新整理|更新樹狀檢視，以反映自上次顯示節點以來可能發生的任何變更。|  
|Delete|從樹狀檢視移除選取的節點。 **Note:**  只有 \[**SharePoint 連接**\] 節點底下所列的 SharePoint 連接才會啟用此命令。|  
|屬性|在 \[**屬性**\] 視窗中顯示所選節點的可用屬性。  屬性全部都是唯讀的，而且並非所有節點都有相關聯的屬性。|  
|加入連接|可讓您指定要瀏覽的 SharePoint 網站。  此命令適用於 \[**SharePoint 連接**\] 節點和子網站節點。|  
|在瀏覽器中檢視|在 Web 瀏覽器中顯示選取的清單。  此命令適用於 \[**清單和程式庫**\] 中 \[**清單**\] 節點下的某些清單。|  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[如何：新增或移除 SharePoint 連線](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|說明將新的 SharePoint 網站加入至 \[**伺服器總管**\] 中的 \[**SharePoint 連接**\] 節點所需的步驟。|  
  
## 請參閱  
 [伺服器總管](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  