---
title: "提供專案項目中的封裝和部署資訊"
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
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "功能屬性 [Visual Studio 中的 SharePoint 程式開發]"
  - "功能接收器 [Visual Studio 中的 SharePoint 程式開發]"
  - "專案輸出參考 [Visual Studio 中的 SharePoint 程式開發]"
  - "安全控制項 [Visual Studio 中的 SharePoint 程式開發]"
  - "Visual Studio 中的 SharePoint 開發, 進階封裝工具"
  - "Visual Studio 中的 SharePoint 開發, 功能屬性"
  - "Visual Studio 中的 SharePoint 開發, 功能接收器"
  - "Visual Studio 中的 SharePoint 開發, 專案輸出參考"
  - "Visual Studio 中的 SharePoint 開發, 安全控制項"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 提供專案項目中的封裝和部署資訊
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的所有 SharePoint 專案項目都具有屬性；在將專案部署至 SharePoint 時，您可以使用這些屬性來提供額外的資料。  這些屬性如下所示：  
  
-   功能屬性  
  
-   功能接收器  
  
-   專案輸出參考  
  
-   安全控制項項目  
  
 這些屬性都會顯示於 \[**屬性**\] 視窗中。  
  
## 功能屬性  
 使用 \[**功能屬性**\] 屬性來指定功能所使用的資料。  功能屬性資料是將功能部署至 SharePoint 時功能中所含的一組值 \(儲存為索引鍵\/值組\)。  部署功能之後，您便可以在程式中存取這些屬性值。  
  
 當您在專案項目中加入功能屬性值時，該值就會以元素型式加入至項目功能的資訊清單中。  例如，在「商務資料連接」\(BDC\) 模型專案中，ModelFileName 功能屬性會顯示為：  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 在您設定「功能屬性」值之後，該值會以 FeatureProperty 元素的型式加入至專案的 .spdata 檔案中。  如需存取 SharePoint 中屬性的詳細資訊，請參閱 [SPFeaturePropertyCollection Class](http://go.microsoft.com/fwlink/?LinkId=177391)。  
  
 在功能資訊清單中，將所有專案項目的相同功能屬性值合併在一起。  然而，如果兩個不同的專案項目將不同的值指定給相同的功能屬性索引鍵，則會發生驗證錯誤。  
  
 若要將功能屬性直接加入至功能檔案 \(\*.feature\)，請呼叫 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 物件模型方法 <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>。  如果您使用此方法，請注意在「功能屬性」中加入相同功能屬性值的規則同樣適用於直接加入至功能檔案的屬性。  
  
## 功能接收器  
 功能接收器是專案項目所含功能發生特定事件時執行的程式碼。  例如，您可以定義在安裝、啟動或升級功能時執行的功能接收器。  加入功能接收器的方法之一是直接將其加入至功能，請參閱[逐步解說：新增功能事件接收器](../sharepoint/walkthrough-add-feature-event-receivers.md)中的說明。  另一種方法是在 \[**功能接收器**\] 屬性中參考功能接收器的類別名稱和組件。  
  
### 直接方法  
 當您將功能接收器直接加入至功能時，\[方案總管\] 中的 \[**功能**\] 節點下方會出現一個程式碼檔。  因此當您建置 SharePoint 方案時，該程式碼會編譯成組件並部署至 SharePoint。  根據預設，功能屬性 \[**接收器組件**\] 和 \[**接收器類別**\] 會參考類別名稱和組件。  
  
### 參考方法  
 另外一種加入功能接收器的方法：使用專案項目的 \[**功能接收器**\] 屬性來參考功能接收器組件。  \[功能接收器\] 屬性值具有兩個子屬性：\[**組件**\] 和 \[**類別名稱**\]。  組件必須使用其完整限定的「強式」名稱，且類別名稱必須為完整的型別名稱。  如需詳細資訊，請參閱 [強式名稱的組件](http://go.microsoft.com/fwlink/?LinkID=169573)。  將方案部署至 SharePoint 之後，功能會使用參考的功能接收器來處理功能事件。  
  
 在方案建置階段，功能中的功能接收器屬性 \(Property\) 值與其專案會合併，以便設定 SharePoint 方案 \(.wsp\) 檔案之功能資訊清單中「功能」元素的 ReceiverAssembly 和 ReceiverClass 屬性 \(Attribute\)。  因此，如果同時指定專案項目與功能的 \[組件\] 和 \[類別名稱\] 屬性值，則專案項目與功能屬性值必須相符。  如果值不相符，則您會收到驗證錯誤。  如果您要讓專案項目參考非功能所使用的功能接收器組件，則將其移至另一個功能。  
  
 如果您參考了伺服器上不存在的功能接收器組件，則還必須在封裝中包含其組件檔；[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不會為您加入組件檔。  當您部署功能時，組件檔會複製至系統的 [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] 或 SharePoint 實體目錄中的 Bin 資料夾中。  如需詳細資訊，請參閱 [如何：新增與移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 如需功能接收器的詳細資訊，請參閱 [功能事件接收器](http://go.microsoft.com/fwlink/?LinkID=169574) 和 [功能事件](http://go.microsoft.com/fwlink/?LinkID=169575)。  
  
## 專案輸出參考  
 \[專案輸出參考\] 屬性會指定您的專案項目執行時所需的相依性，例如組件。  例如，假設您的方案具有 BDC 專案和類別專案。  如果 BDC 專案對類別專案輸出的組件具有相依性，您就可以在 BDC 專案之 \[專案輸出參考\] 屬性中參考此組件。  封裝 BDC 專案時，相依組件會包含在封裝中。  
  
 專案輸出參考通常來說是組件，但在某些情況下 \(例如，Silverlight 專案\) 可以是其他檔案類型。  
  
 如需詳細資訊，請參閱[如何：加入專案輸出參考](../sharepoint/how-to-add-a-project-output-reference.md)。  
  
## 安全控制項項目  
 SharePoint 提供一項稱為安全控制項項目的安全性機制，用來限制未受信任的使用者對特定控制項的存取。  根據設計，SharePoint 允許未受信任的使用者在 SharePoint 伺服器上上載和建立 ASPX 頁面。  為了防止這些使用者將不安全的程式碼加入至 ASPX 頁面，SharePoint 會限制他們對「*安全控制項*」\(Safe Control\) 的存取。  安全控制項是指定為安全的 ASPX 控制項和 Web 組件，您站台上任何使用者均可使用。  如需詳細資訊，請參閱 [步驟 4：將網頁組件加入至安全性控制目錄](http://go.microsoft.com/fwlink/?LinkID=171014)。  
  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的每個 SharePoint 專案項目都有一個名為 \[**安全控制項項目**\] 的屬性，其擁有兩個布林子屬性 : \[**安全性**\] 和 \[**防止指令碼的安全**\]。  安全屬性會指定未受信任的使用者能否存取控制項。  \[防止指令碼威脅\] 屬性則指定未受信任的使用者能否檢視及變更控制項的屬性。  
  
 安全控制項項目的參考需針對個別組件進行。  您可以在專案項目的 \[**安全控制項項目**\] 屬性中輸入安全控制項項目，以便將它們加入至專案的組件。  然而，您也可以在將其他組件加入至封裝時，透過 \[**封裝設計工具**\] 中的 \[**進階**\] 索引標籤，將安全控制項項目加入至專案的組件。  如需詳細資訊，請參閱 [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md) 或 [註冊 Web 組件組譯碼作為安全控制項](http://go.microsoft.com/fwlink/?LinkID=171013)。  
  
### 安全控制項的 XML 項目  
 當您將安全控制項項目加入至專案項目或專案的組件時，參考會以下列格式寫入至封裝資訊清單：  
  
```  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  