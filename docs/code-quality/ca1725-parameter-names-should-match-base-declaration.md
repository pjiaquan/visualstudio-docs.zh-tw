---
title: "CA1725：參數名稱應該符合基底宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1725：參數名稱應該符合基底宣告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的方法覆寫中的參數名稱不符合方法的基底宣告中的參數名稱，或是方法的介面宣告中的參數名稱。  
  
## 規則描述  
 在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。  與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請重新命名參數以符合基底宣告。  此修正為 COM 可見方法的中斷變更。  
  
## 隱藏警告的時機  
 除了先前所提供之程式庫中的 COM 可見方法外，請勿隱藏這項規則的警告。