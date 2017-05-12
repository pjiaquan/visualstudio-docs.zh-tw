---
title: "&lt;進入點&gt; 項目 (Visual Studio 中的 Office 程式開發)"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<進入點> 項目"
  - "<進入點> 項目"
  - "entryPoint 項目"
ms.assetid: 0c9d22d0-0852-4260-89c6-b83f24e48793
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;進入點&gt; 項目 (Visual Studio 中的 Office 程式開發)
  每個 `vstav3`  命名空間的 `entryPoint` 項目都會識別出安裝這個 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式時應該執行的自訂組件。  
  
## 語法  
  
```  
<entryPoint class>  
    <assemblyIdentity />  
</entryPoint>  
```  
  
## 項目和屬性  
 `entryPoint` 項目是必要的，且位於 `vstav3`  命名空間。  
  
 每個 `entryPoint` 項目只可以包含一個自訂組件。 在應用程式資訊清單中可以定義多個 `entryPoint` 項目。  
  
 `entryPoint` 項目具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`class`|必要項。 識別要執行的自訂組件。 這個屬性的語法是 *NamespaceName.ClassName*。|  
  
 `entryPoint` 具有下列項目。  
  
### assemblyIdentity  
 必要項。`vstav3`  命名空間中的 `assemblyIdentity` 項目參考 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 應用程式資訊清單中的現有 `assemblyIdentity` 項目。  
  
 `assemblyIdentity` 的角色及其屬性是在 [&#60;assemblyIdentity&#62; 項目 &#40;ClickOnce 應用程式&#41;](~/deployment/assemblyidentity-element-clickonce-application.md) 中定義。  
  
## 文件層級自訂範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之文件層級 Office 解決方案應用程式資訊清單中的 `entryPoint` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 所部署之應用程式層級 Office 解決方案應用程式資訊清單中的 `entryPoint` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)中所提供之完整範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  