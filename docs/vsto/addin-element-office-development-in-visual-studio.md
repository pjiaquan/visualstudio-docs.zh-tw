---
title: "&lt;addin&gt; 項目 (Visual Studio 中的 Office 程式開發) | Microsoft Docs"
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
  - "應用程式資訊清單 [Visual Studio 中的 Office 程式開發]，<addIn> 項目"
  - "addin 項目"
  - "<addin> 項目"
ms.assetid: 4abec4c3-8c7c-4b2b-9128-79fa4e863281
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;addin&gt; 項目 (Visual Studio 中的 Office 程式開發)
  `vstav3`  命名空間的 `addin` 項目包含 Microsoft Office VSTO 增益集和使用 Visual Studio 開發之文件層級自訂的特定資訊。  
  
## 語法  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## 項目和屬性  
 `vstav3`  命名空間的 `addin` 項目包含 Office 方案和 Microsoft Office 應用程式的相關資訊。 此項目必須位於下列命名空間：`vstav3=urn:schemas-microsoft-com:vsta.v3`。 子項目也必須在這個命名空間中。  
  
 `addin` 項目沒有任何屬性。  
  
 `addin` 項目具有下列子項目。  
  
### entryPoints  
 必要項。[&#60;entryPoints&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md) 中會說明 `entryPoints` 項目。  
  
### 更新  
 必要項。[&#60;update&#62; 元素 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/update-element-office-development-in-visual-studio.md) 中會說明 `update` 項目。  
  
### postActions  
 選擇項。[&#60;postActions&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/postactions-element-office-development-in-visual-studio.md) 中會說明 `postActions` 項目。  
  
### 應用程式  
 必要項。[&#60;應用程式&#62; 項目 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/application-element-office-development-in-visual-studio.md) 中會說明 `application` 項目。  
  
## 文件層級自訂範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之文件層級 Office 方案中的 `addin` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## VSTO 增益集範例  
  
### 描述  
 下列程式碼範例說明使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署之應用程式層級 Office 方案中的 `addin` 項目。 這個程式碼範例是 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md) 中所提供之較大範例的一部分。  
  
### 程式碼  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## 請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)  
  
  