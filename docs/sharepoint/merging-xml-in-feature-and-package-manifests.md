---
title: "合併功能和封裝資訊清單中的 XML | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 開發, 封裝"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 合併功能和封裝資訊清單中的 XML
  功能和封裝由 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 資訊清單檔定義。  這些封裝的資訊清單是設計工具中所產生資料與資訊清單範本中使用者所輸入自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 的組合。  封裝時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會將自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 陳述式與設計工具提供的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 合併，來構成封裝的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 資訊清單檔。  除了稍後在「合併例外狀況」中註明的例外狀況，將合併類似的項目以避免您將檔案部署至 SharePoint 之後發生 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 驗證錯誤，並讓資訊清單檔更小且更有效率。  
  
## 修改資訊清單  
 只有當您停用功能或封裝設計工具之後，才可以直接修改封裝的資訊清單檔。  然而，您可以透過功能和封裝設計工具或 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 編輯器，將自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 項目手動加入至資訊清單範本。  如需詳細資訊，請參閱[如何：自訂 SharePoint 功能](../sharepoint/how-to-customize-a-sharepoint-feature.md)與[如何：自訂 SharePoint 方案套件](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)。  
  
## 功能和封裝資訊清單合併程序  
 將自訂項目與設計工具提供的項目組合在一起時，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會使用下列程序。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 檢查每個項目是否具有唯一的索引鍵值。  如果項目沒有唯一的索引鍵值，則會將其附加至封裝的資訊清單檔。  同樣地，具有多個索引鍵的項目無法合併。  因此，會將其附加至資訊清單檔。  
  
 如果項目具有唯一的索引鍵，則 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會比較設計工具與自訂索引鍵的值。  如果值相符，則會將其合併成單一值。  如果值不同，則會捨棄設計工具索引鍵值並使用自訂索引鍵值。  同時也會合併集合。  例如，如果設計工具產生的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 和自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 都含有「組件」集合，則封裝的資訊清單只包含一個「組件」集合。  
  
## 合併例外狀況  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 將具有類似自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 項目的大部分設計工具 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 項目合併到一起，前提是這些項目具有單一且唯一的識別屬性。  然而，部分項目缺少 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 合併所需的唯一識別項。  這些項目稱為「*合併例外狀況*」\(Merge Exception\)。  在這些情況下，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 不會將自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 項目與設計工具提供的 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 項目合併到一起，而是會將它們附加至封裝的資訊清單檔。  
  
 以下是功能和封裝 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 資訊清單檔的合併例外狀況清單。  
  
|設計工具|XML 項目|  
|----------|------------|  
|功能設計工具|ActivationDependency|  
|功能設計工具|UpgradeAction|  
|封裝設計工具|SafeControl|  
|封裝設計工具|CodeAccessSecurity|  
  
## 功能資訊清單項目  
 下表為可合併的所有功能資訊清單項目及其可用於比對之唯一索引鍵的清單。  
  
|項目名稱|唯一索引鍵|  
|----------|-----------|  
|Feature \(所有屬性\)|*Attribute Name* \(Feature 項目的每個屬性名稱都是唯一的索引鍵\)。|  
|ElementFile|位置|  
|ElementManifests\/ElementManifest|位置|  
|Properties\/Property|Key|  
|CustomUpgradeAction|名稱|  
|CustomUpgradeActionParameter|名稱|  
  
> [!NOTE]  
>  由於修改 CustomUpgradeAction 項目的唯一方式是在自訂 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 編輯器中進行修改，因此未合併的效果會很差。  
  
## 封裝資訊清單項目  
 下表為可合併的所有封裝資訊清單項目及其可用於比對之唯一索引鍵的清單。  
  
|項目名稱|唯一索引鍵|  
|----------|-----------|  
|Solution \(所有屬性\)|*Attribute Name* \(Solution 項目的每個屬性名稱都是唯一的索引鍵\)。|  
|ApplicationResourceFiles\/ApplicationResourceFile|位置|  
|Assemblies\/Assembly|位置|  
|ClassResources\/ClassResource|位置|  
|DwpFiles\/DwpFile|位置|  
|FeatureManifests\/FeatureManifest|位置|  
|Resources\/Resource|位置|  
|RootFiles\/RootFile|位置|  
|SiteDefinitionManifests\/SiteDefinitionManifest|位置|  
|WebTempFile|位置|  
|TemplateFiles\/TemplateFile|位置|  
|SolutionDependency|SolutionID|  
  
## 手動加入部署的檔案  
 部分資訊清單項目 \(例如，ApplicationResourceFile 和 DwpFiles\) 會指定含有檔名的位置。  然而，將檔名項目加入至資訊清單範本並不會將基礎檔案加入至封裝。  您必須將檔案加入至專案，以將其納入封裝並依情況設定其 \[部署類型\] 屬性。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  