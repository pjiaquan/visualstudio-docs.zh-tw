---
title: "&lt;RelatedProducts&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts> 項目 [啟動載入器]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;RelatedProducts&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`RelatedProducts` 項目定義相依或包括在目前產品中的其他產品。  
  
## 語法  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## 項目和屬性  
 `RelatedProducts` 項目是 `Product` 項目的子系。  它沒有屬性。  
  
## DependsOnProduct  
 `DependsOnProduct` 項目表示目前產品相依於具名產品，而且該具名產品應該在目前產品之前安裝。  它是 `RelatedProducts` 項目的子項目。  `RelatedProducts` 項目可以具有一個或多個 `DependsOnProduct` 項目。  
  
 `DependsOnProduct` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Code`|如 `Product` 項目的 `ProductCode` 屬性指定的，所包含產品的代碼名稱。  如需詳細資訊，請參閱 [\<Product\> 項目](../deployment/product-element-bootstrapper.md)。|  
  
## EitherProducts  
 `EitherProducts` 項目會定義零個或多個 `DependsOnProduct` 項目，而且沒有任何屬性。  在安裝目前產品之前，必須在這個集合中安裝至少一個 `DependsOnProduct`。  `RelatedProducts` 項目可以有零個或多個 `EitherProducts` 項目。  
  
## IncludesProduct  
 `IncludesProduct` 項目表示產品包含在目前的安裝中，不需要個別的安裝。  它是 `RelatedProducts` 項目的子項目。  `RelatedProducts` 項目可以具有一個或多個 `IncludesProduct` 項目。  
  
 `IncludesProduct` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Code`|如 `Product` 項目的 `ProductCode` 屬性指定的，所包含產品的代碼名稱。  如需詳細資訊，請參閱 [\<Product\> 項目](../deployment/product-element-bootstrapper.md)。|  
  
## 範例  
 在下列程式碼範例中，指定以 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 安裝 Microsoft Installer，因此不會需要個別安裝。  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## 請參閱  
 [\<Product\> 項目](../deployment/product-element-bootstrapper.md)