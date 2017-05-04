---
title: "當地語系化 SharePoint 方案 | Microsoft Docs"
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
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "全球化 [Visual Studio 中的 SharePoint 程式開發]"
  - "當地語系化 [Visual Studio 中的 SharePoint 開發]"
  - "Visual Studio 中的 SharePoint 開發，當地語系化"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 當地語系化 SharePoint 方案
  準備讓您的應用程式能在全球範圍內使用的流程稱為當地語系化。  當地語系化是將資源轉譯為特定的文化特性。  如需詳細資訊，請參閱[全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)。  本主題概要介紹如何當地語系化 SharePoint 方案。  
  
 若要當地語系化方案，您要從程式碼中移除硬式編碼字串，並將它們抽出彙為資源檔。  資源檔是副檔名為 .resx 的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 架構檔案。  資源檔包含您方案中所使用字串的轉譯版本。  如需詳細資訊，請參閱[桌面應用程式中的資源](http://go.microsoft.com/fwlink/?LinkID=155844)。  
  
> [!NOTE]  
>  請只在 SharePoint 方案資源檔中加入字串資源。  儘管 \[資源編輯器\] 可讓您加入非字串資源，但是非字串資源無法部署至 SharePoint。  
  
## 資源檔  
 有三種資源檔：預設、語言中性和語言特定資源檔。  
  
|資源檔類型|描述|  
|-----------|--------|  
|Default|也稱為後援資源，預設資源檔包含預設文化特性的當地語系化字串 \(例如英文\)。  如果找不到指定語言的當地語系化資源檔，就會使用預設資源檔。  預設資源沒有個別檔案，它們都儲存在主應用程式組件中。|  
|語言中性|包含某種語言 \(非特定文化特性\) 之當地語系化字串的資源檔。  例如，"fr" 表示法文。|  
|語言特定|包含某種語言及文化特性之當地語系化字串的資源檔。  例如，"fr\-CA" 表示加拿大法文。|  
  
 如需詳細資訊，請參閱[當地語系化資源的階層式組織](http://go.microsoft.com/fwlink/?LinkId=178360)。  
  
 若要在以 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 開發的 SharePoint 專案中指定預設資源檔，請在加入資源檔時選取 \[**加入資源**\] 對話方塊之文化特性清單中的 \[**不因語言而異 \(不因國家\/地區別而異\)**\]。  
  
## 當地語系化 Visual Studio SharePoint 方案  
 在您當地語系化方案時，應將專案顯示給使用者的所有文字資訊都納入考慮。  必須轉譯告知性訊息、錯誤訊息和 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 字串，並將那些轉譯放置在資源檔中。  
  
 資源檔中的每個字串都有唯一的識別項。  每個資源檔中的轉譯字串也請使用相同的識別項。  例如，如果 "String1" 是預設資源檔中第一個字串的識別項，則針對語言特定資源檔中的第一個字串使用相同的識別項。  
  
 您通常會當地語系化 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 應用程式中的三個區域：功能、ASPX 頁面標記和程式碼。  為了進行說明，下列各節假設您要將 SharePoint 方案當地語系化為德文和日文。  預設語言為英文。  
  
### 當地語系化功能  
 若要當地語系化功能，您必須將功能的硬式編碼標題和描述取代為參考當地語系化資源檔中已轉譯標題和字串的運算式。  請在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 \[**功能設計工具**\] 中進行此變更。  如需詳細資訊，請參閱 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)。  
  
 若要將英文功能當地語系化為德文和日文，您需要將三個「資源檔」專案項目加入至專案，分別用於英文、德文和日文。  ASPX 標記或程式碼無法使用功能資源檔來當地語系化，它們需要使用個別的資源檔。  
  
 建立功能資源檔之後，向其加入已轉譯的字串。  使用下列格式的運算式來存取當地語系化的字串：  
  
```  
$Resources:String ID  
```  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的功能資源始終稱為「資源」。  如果您選取不因語言而異以外的語言，則文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 會加入至資源檔名稱。  例如，如果您加入不因語言而異 \(預設\) 的功能資源檔，就稱為 Resources.resx。  如果您透過選取日文 \(日本\) 文化特性來加入語言特定功能資源，則該檔案稱為 Resources.ja\-JP.resx。  系統會自動指派功能資源檔名稱，您無法變更該名稱。  
  
 功能資源的範圍對於功能資源所加入至的功能而言是區域性的。  若要建立可由方案中任何功能或元素檔案使用的資源，請加入 \[**全域資源檔**\] 專案項目而非功能資源檔。  \[**全域資源檔**\] 專案項目位於 \[**加入新項目**\] 對話方塊中 \[**SharePoint**\] 下方的 \[**2010**\] 資料夾中。  將全域資源檔部署至 SharePoint 根資料夾的 \\Resources 資料夾。  
  
### 當地語系化 ASPX 頁面標記  
 若要當地語系化 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 頁面，請將三個「資源檔」專案項目加入至專案，分別用於英文、德文和日文。  如果除了標記以外，不需要當地語系化程式碼，您可以改為加入全域資源檔案。  
  
 提供預設語言資源檔的名稱。  對當地語系化的資源檔提供附加有語言特定文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 的相同名稱。  例如，德文為 MyAppResources.de\-DE.resx 而日文為 MyAppResources.ja\-JP.resx。  
  
 將每個資源檔的 \[**部署類型**\] 屬性設定為 \[**AppGlobalResource**\]。  如此會將資源檔部署至 App\_GlobalResources 資料夾，在該資料夾中資源檔可用於方案中的所有 ASPX 頁面和控制項。  App\_GlobalResources 資料夾位於 C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<port number\>\\App\_GlobalResources 中。  
  
> [!NOTE]  
>  如果您使用非全域資源檔，則將它們移入專案項目資料夾中，以啟用 \[部署類型\] 屬性及其他 SharePoint 特定屬性。  
  
 ASPX 標記資源檔也可用來當地語系化程式碼。  如果您使用資源除了當地語系化 ASPX 標記以外還當地語系化程式碼，則將每個檔案的 \[建置動作\] 屬性設定保留為 \[內嵌資源\]，以將資源編譯成附屬組件。  然而，如果您使用資源檔只當地語系化標記，則可以選擇將 \[建置動作\] 變更為 \[內容\]，以防止將檔案編譯成主應用程式組件。  
  
 將 ASPX 頁面和控制項標記中的所有硬式編碼屬性字串取代為下列格式的運算式：  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 對於文字型的 ASPX，使用下列格式的運算式：  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例如：  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 如需詳細資訊，請參閱 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)。  
  
### 當地語系化程式碼  
 除了當地語系化「功能」字串和 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 標記以外，您還必須當地語系化方案程式碼中出現的訊息字串和錯誤字串。  當地語系化的告知性訊息和錯誤訊息是包含在附屬組件中。  附屬組件包含使用者可見的字串，例如類似例外狀況的 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文字和輸出訊息。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 使用標準 .NET Framework 中樞和輪輻模型。  該中樞或主程式組件包含預設語言資源。  該輪輻或附屬組件包含語言特定資源。  如需詳細資訊，請參閱[封裝和部署資源](http://go.microsoft.com/fwlink/?LinkId=179280)。  附屬組件編譯自資源 \(.resx\) 檔。  當您將語言特定的資源檔加入至專案及方案套件時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將資源檔編譯成名為 *Project Name*.resources.dll 的附屬組件。  
  
 如同 ASPX 標記，透過將個別的「資源檔」專案項目加入至專案來當地語系化 SharePoint 應用程式程式碼；其中預設語言使用一個專案項目，每個當地語系化的語言也各使用一個專案項目。  但如前所述，如果您已擁有用於當地語系化 ASPX 標記的資源檔，則可以重複使用它們來當地語系化程式碼。  如果您需要建立資源檔，請對預設語言資源檔提供您所選擇且附加有副檔名 .resx 的名稱。  將當地語系化的資源檔命名為附加有語言特定文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 的相同名稱。  將每個資源檔的 \[建置動作\] 屬性設定為 \[內嵌資源\]，以啟用附屬資源組件的建立。  
  
 若要建立附屬組件，請建置專案然後透過 \[**封裝設計工具**\] 的 \[**進階**\] 索引標籤，來加入檔案做為其他組件。  加入組件時，在「位置」路徑之前加上文化特性 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 資料夾，例如 de\-DE\\*Project Item Name*.resources.dll。  如此便可讓套件包含具有相同名稱的檔案。  
  
 在您的程式碼中，使用下列語法將硬式編碼字串取代為對方法 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 的呼叫：  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 如需詳細資訊，請參閱 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)。  
  
#### Web 組件程式碼當地語系化  
 Web 組件包含一個自訂屬性編輯器功能，該功能含有使用硬式編碼字串的程式碼屬性，例如 WebDisplayName、Category 和 WebDescription。  若要取代這些屬性的字串值，請建立一個衍生自屬性類別的個別類別。  在那些類別中，設定屬性 \(Attribute\) 的屬性 \(Property\)。  屬性 \(Attribute\) 的屬性 \(Property\) 視基底類別而定。  例如，WebDisplayName 屬性 \(Attribute\) 的屬性 \(Property\) 為 DisplayNameValue，而 WebDescription 屬性 \(Attribute\) 的屬性 \(Property\) 為 DescriptionValue。  
  
 在衍生的類別中，參考資源檔和 ResourceManager 物件中的字串 ID，以取得字串 ID 的當地語系化值。  將此值傳回至屬性 \(Property\) 編輯器屬性 \(Attribute\)。  
  
## 請參閱  
 [如何：當地語系化功能](../sharepoint/how-to-localize-a-feature.md)   
 [如何：當地語系化 ASPX 標記](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：當地語系化程式碼](../sharepoint/how-to-localize-code.md)   
 [如何：新增資源檔](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：使用資源檔來指定當地語系化名稱、屬性和使用權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  