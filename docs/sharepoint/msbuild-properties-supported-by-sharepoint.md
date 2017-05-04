---
title: "SharePoint 支援的 MSBuild 屬性 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 開發, MSBuild 屬性"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# SharePoint 支援的 MSBuild 屬性
  Microsoft.VisualStudio.SharePoint.targets 檔案、專案檔或專案使用者檔案中定義的任何 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性都可用於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 專案中。  除了專案提供的一般 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性以外，SharePoint 還會定義專屬於 SharePoint 專案的其他屬性。  
  
 如需常用的 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性的清單，請參閱 [一般 MSBuild 專案屬性](http://go.microsoft.com/fwlink/?LinkID=168687)。  如需您的程式語言所支援屬性的完整清單，請查詢 .targets 檔案、專案檔 \(.csproj 或 .vbproj\) 或專案使用者檔案 \(csproj.user 或 .vbproj.user\)。  
  
## 專屬於 SharePoint 的 MSBuild 屬性  
 下表列出特別適用於 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中 SharePoint 專案的 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 屬性。  存在其他屬性，但是它們僅供內部使用。  
  
|屬性名稱|說明|  
|----------|--------|  
|SharePointSiteUrl|代表 SharePoint 網站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 的字串。|  
|SandboxedSolution|說明方案是否為沙箱化方案的布林值。|  
|ActiveDeploymentConfiguration|現用部署組態。|  
|IncludeAssemblyInPackage|說明組件是否包含在封裝檔案中的布林值。|  
|PreDeploymentCommand|代表要在預先部署命令步驟中執行之命令的字串值。|  
|PostDeploymentCommand|代表要在部署後命令步驟中執行之命令的字串值。|  
|CustomBeforeSharePointTargets|代表 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目標檔路徑的字串。  如果目標檔存在且已定義，則會在匯入任何 SharePoint 目標資料之前匯入它。  此屬性可讓您預先定義封裝相關的屬性而無需修改隨附的 SharePoint 目標檔來自訂封裝程序，同時目標檔仍適用於所有 SharePoint 專案。|  
|CustomAfterSharePointTargets|代表 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目標檔路徑的字串。  如果目標檔存在且已定義，則會在匯入所有 SharePoint 目標資料之後匯入它。  此屬性可讓您覆寫封裝相關的屬性和目標而無需修改隨附的 SharePoint 目標檔來自訂封裝程序，同時目標檔仍適用於所有 SharePoint 專案。|  
|LayoutPath|代表加入至 .wsp 檔案之前暫時放置每個待封裝檔案之根目錄的字串。  此路徑有助於了解您會何時覆寫 BeforeLayout 和 AfterLayout 目標來加入、移除或修改待封裝的檔案，原因是您可以使用它來改變 .wsp 檔案的內容。|  
|BasePackagePath|代表放置封裝之資料夾的字串。  此值使用專案的輸出目錄，例如 Bin\\Debug。|  
|PackageExtension|代表附加至封裝之副檔名的字串。  預設值為 wsp。|  
|AssemblyDeploymentTarget|代表 SharePoint 伺服器上部署專案組件所在位置的字串。  其值為 GlobalAssemblyCache \(預設值\) 或 WebApplication。  也可以在 \[屬性\] 視窗中設定此屬性。|  
|PackageWithValidation|指定是否在封裝之前執行驗證的布林值。  此屬性可讓您在建置「封裝」期間忽略驗證錯誤。|  
|ValidatePackageDependsOn|定義執行 ValidatePackage 目標之前所執行之其他目標的字串。|  
|TokenReplacementFileExensions|定義封裝期間語彙基元遭取代之檔案的字串。|  
  
## 使用屬性頁面中的 MSBuild 屬性  
 為了方便日後的調整，您可以在 \[SharePoint 屬性\] 頁面上使用 SharePoint 屬性做為引數，而不需要使用 \[**預先部署命令列**\] 和 \[**部署後命令列**\] 方塊中的硬式編碼字串。  例如，您可以改為使用 `$(SharePointSiteUrl)`，而不需要為 SharePoint 網站指定特定的 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 字串。  
  
> [!NOTE]  
>  您可以使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 變數語法 `$(`*propertyName*`)` 或環境變數語法 `%`*propertyName*`%` 來指定屬性。  
  
## 請參閱  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  
  
  