---
title: "如何：為特定的清單執行個體建立事件接收器 | Microsoft Docs"
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
  - "事件接收器 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 事件接收器"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：為特定的清單執行個體建立事件接收器
  清單執行個體事件接收器會回應在清單定義的任何執行個體中發生的事件。  雖然事件接收器範本不會啟用特定清單執行個體的目標，您還是可以修改以清單定義為範圍的事件接收器，以便回應特定清單執行個體中的事件。  
  
 若要以特定清單執行個體為目標，請在事件接收器的 Elements.xml 中，以 `ListUrl` 取代 `ListTemplateId`，然後加入清單執行個體的 URL。  
  
## 建立清單執行個體事件接收器  
 下列步驟示範如何修改清單項目事件接收器，以便只回應自訂公告清單執行個體中發生的事件。  
  
#### 若要修改事件接收器來回應特定的清單執行個體  
  
1.  在瀏覽器中開啟 SharePoint 網站。  
  
2.  在巡覽窗格中， \[**清單**\] 連結。  
  
3.  在 \[**所有網站內容**\] 頁面上，選擇 \[**建立**\] 連結。  
  
4.  在 \[**建立**\] 對話方塊中，選擇 \[**公告**\] 型別，並將公告命名為 TestAnnouncements，然後選擇 \[**建立**\] 按鈕。  
  
5.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，建立事件接收器專案。  
  
6.  在 \[**您要何種類型的事件接收器?**\] 清單中，選取 \[**清單項目事件**\]。  
  
    > [!NOTE]  
    >  您也可以選取以清單定義為範圍的任何其他種類的事件接收器，例如 \[**清單電子郵件事件**\] 或 \[**清單工作流程事件**\]。  
  
7.  在 \[**哪些項目應為事件來源?**\] 清單中，選取 \[**公告**\]。  
  
8.  在 \[**處理下列事件**\] 清單中，選取 \[**已加入一個項目**\] 核取方塊，然後選擇 \[**結束**\] 按鈕。  
  
9. 在 \[**方案總管**\] 的 EventReceiver1 底下，開啟 Elements.xml。  
  
     藉由使用下列程式碼，事件接收器目前會參考公告清單定義：  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     請將這行改變為以下文字：  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     這樣會導向事件接收器，使其只回應您在剛才建立的新 **TestAnnouncements** 公告清單中所發生的事件。  您可以變更 `ListURL` 屬性來參考 SharePoint 伺服器上的任何清單執行個體。  
  
10. 開啟事件接收器的程式碼檔，然後在 ItemAdding 方法中放入中斷點。  
  
11. 選擇 F5 鍵以建置和執行方案。  
  
12. 在 SharePoint 中，選擇巡覽窗格中的 \[**TestAnnouncements**\] 連結。  
  
13. 選擇 \[**新增公告**\] 連結。  
  
14. 輸入公告的標題，然後選擇 \[**儲存**\] 按鈕。  
  
     請注意，當新的項目加入至自訂公告清單時，就會遇到中斷點。  
  
15. 選擇 F5 鍵繼續。  
  
16. 在巡覽窗格中，選擇 \[**清單**\] 連結，然後選擇 \[**公告**\] 連結。  
  
17. 加入新的公告。  
  
     請注意，事件接收器不會在新的公告上觸發，因為此接收器設定為只回應自訂公告清單執行個體 \[**TestAnnouncements**\] 中的事件。  
  
## 請參閱  
 [如何：建立事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  