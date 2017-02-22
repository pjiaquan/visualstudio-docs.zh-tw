---
title: "&lt;Schedules&gt; 項目 (啟動載入器) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> 項目 [啟動載入器]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Schedules&gt; 項目 (啟動載入器)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Schedules` 項目含有 `Schedule` 項目，根據 `Command` 項目所定義的命令指定執行的特定時間。  
  
## 語法  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## 項目和屬性  
 `Schedules` 項目是 `Product` 項目的子系。  每個 `Product` 項目最多只能有一個 `Schedules` 項目。  `Schedules` 項目沒有任何屬性。  
  
## Schedule  
 `Schedule` 項目是 `Schedules` 項目的子系。  `Schedules` 項目必須至少有一個 `Schedule` 項目。  
  
 `Schedule` 具有下列屬性。  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要項。  排程項目的名稱。  此項對應於 `Command` 項目的 `ScheduleName` 屬性。  當 `Command` 參考具名排程時，就只會在 `Schedule` 項目指示的時間執行。  排程也可以和 `FailIf` 及 `BypassIf` 項目產生關聯，如此便可限制這些條件測試在指定的排程上執行。  如需詳細資訊，請參閱 [\<Commands\> 項目](../deployment/commands-element-bootstrapper.md)。|  
  
 指定的 `Schedule` 項目可以只有下列其中一個子項目。  
  
## BuildList  
 `BuildList` 項目會指示安裝程式在啟動載入應用程式啟動之後，立即執行一項命令。  
  
## BeforePackage  
 `BeforePackage` 項目會指示安裝程式在安裝指定的套件前，執行一項命令。  
  
## AfterPackage  
 `AfterPackage` 項目會指示安裝程式在安裝指定的套件後，執行一項命令。  
  
## 請參閱  
 [\<Product\> 項目](../deployment/product-element-bootstrapper.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)