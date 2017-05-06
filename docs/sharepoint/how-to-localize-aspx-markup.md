---
title: "如何：當地語系化 ASPX 標記"
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
  - "當地語系化 XML [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發, 當地語系化"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：當地語系化 ASPX 標記
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] \(.aspx\) 頁面通常會使用硬式編碼的字串值。  若要當地語系化這些字串，請將它們取代為參考當地語系化資源的運算式。  
  
## 當地語系化 ASPX 標記  
  
#### 若要當地語系化 ASPX 標記  
  
1.  加入不同的資源檔：一個適用於預設語言，而另一個適用於每種當地語系化的語言。  
  
     如果您只當地語系化標記而不當地語系化程式碼，則加入「全域資源檔」專案項目。  如要您當地語系化程式碼和標記，則加入「資源檔」專案項目。  
  
    1.  若要加入全域資源檔，請在 \[**方案總管**\] 中，開啟 SharePoint 專案項目的捷徑功能表，然後選取 \[**加入**\]、\[**新的項目**\]。  在 SharePoint \[**2010**\] 節點下，選取 \[**全域資源檔**\] 範本。  
  
    2.  若要加入資源檔，請在 \[**方案總管**\] 中，開啟 SharePoint 專案項目的捷徑功能表，然後選取 \[**加入**\]、\[**新的項目**\]。  在 \[**Visual Basic**\] 或 \[**Visual C\#**\] 節點下，選取 \[**資源檔**\] 範本。  
  
    > [!NOTE]  
    >  請務必將資源檔加入至 SharePoint 專案項目中，以啟用 \[部署類型\] 屬性。  此程序的稍後步驟需要這個屬性。  如果您的方案沒有 SharePoint 專案項目，您可以加入空的 SharePoint 專案，並移除其預設 Elements.xml 檔案。  
  
2.  對預設語言資源檔提供您所選擇的名稱，並附加副檔名 .resx，例如 MyAppResources.resx。  針對每個當地語系化的資源檔使用相同的基底名稱，但是會加上文化 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]。  例如，將當地語系化為德文的資源命名為 MyAppResources.de\-DE.resx。  
  
3.  將每個資源檔的 \[**部署類型**\] 屬性的值變更為 \[**AppGlobalResource**\]，以將它們部署至伺服器的 App\_GlobalResources 資料夾。  
  
4.  如果您使用資源時，除了用於 ASPX 標記，還有用於當地語系化程式碼的話，請將每個檔案的 \[**建置動作**\] 屬性設定保留為 \[**內嵌資源**\]。  如果您使用資源檔只用於當地語系化標記，則可以選擇性地將檔案的屬性值變更為 \[**內容**\]。  如需詳細資訊，請參閱[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。  
  
5.  開啟每個資源檔，並且在每個檔案中使用相同的字串 ID 來加入當地語系化的字串。  
  
6.  在 ASPX 頁面或控制項的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 標記中，以使用下列格式的值取代硬式編碼的字串：  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     例如，若要當地語系化應用程式頁面上標籤控制項的文字，您會變更：  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     設為  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  選擇 F5 鍵以建置和執行應用程式。  
  
8.  在 SharePoint 中，變更預設的顯示語言。  
  
     當地語系化的字串會出現在應用程式中。  若要顯示當地語系化資源，SharePoint 伺服器必須已安裝符合資源檔之文化特性的語言套件。  
  
## 請參閱  
 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)  
  
  