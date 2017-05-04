---
title: "如何：當地語系化程式碼 | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "當地語系化程式碼 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 當地語系化"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：當地語系化程式碼
  未當地語系化的程式碼使用硬式編碼字串值。  若要當地語系化程式碼字串，請將它們取代為對參考當地語系化資源之方法 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 的呼叫。  
  
## 當地語系化程式碼  
  
#### 若要當地語系化程式碼  
  
1.  在 \[**方案總管**\] 中，開啟專案項目的捷徑功能表，然後選擇 \[**新增**\]、\[**模組**\]。  
  
     選取 \[**資源檔**\] 範本。  
  
    > [!NOTE]  
    >  請務必將資源檔加入至 SharePoint 專案項目中，好讓 \[部署類型\] 屬性可以使用。  此程序的稍後步驟需要這個屬性。  
  
2.  對預設語言資源檔提供您所選擇的名稱，並附加副檔名 .resx，例如 MyAppResources.resx。  
  
3.  重複步驟一與步驟二，將個別的資源檔加入至 SharePoint 專案項目：一個適用於每個當地語系化的語言。  
  
     針對每個當地語系化的資源檔使用相同的基底名稱，但是會加上文化特性 ID。  例如，將當地語系化為德文的資源命名為 MyAppResources.de\-DE.resx。  
  
4.  開啟每個資源檔並加入當地語系化的字串。  在每個檔案中使用相同的字串ID。  
  
5.  將每個資源檔的 \[**部署類型**\] 屬性之值變更為 \[**AppGlobalResource**\]，將每個檔案部署至伺服器的 App\_GlobalResources 資料夾。  
  
6.  將每個檔案的 \[**建置動作**\] 屬性之值保留為 \[**內嵌資源**\]。  
  
     將內嵌資源編譯為專案的DLL。  
  
7.  建置專案以建立資源附屬 DLL。  
  
8.  在 \[**封裝設計工具**\] 中，選擇 \[**進階**\] 索引標籤，接著加入附屬組件。  
  
9. 在 \[**位置**\] 方塊中，於「位置」路徑前，例如 de\-DE\\*Project Item Name.resources.dll*，加上文化特性 ID 資料夾。  
  
10. 如果您的方案尚未參考 System.Web 組件，則對其加入參考並將您程式碼中的指示詞加入至 <xref:System.Web>。  
  
11. 找出程式碼中所有使用者可見的硬式編碼字串，例如 UI文字、錯誤和訊息文字。  呼叫 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 方法並使用下列語法以取代它們:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. 選擇 F5 鍵以建置和執行應用程式。  
  
13. 在 SharePoint 中，變更預設的顯示語言。  
  
     當地語系化的字串會出現在應用程式中。  若要顯示當地語系化資源，SharePoint 伺服器必須已安裝符合資源檔之文化特性的語言套件。  
  
## 請參閱  
 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)  
  
  