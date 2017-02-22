---
title: "CA2241：必須提供格式化方法的正確引數 | Microsoft Docs"
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
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2241：必須提供格式化方法的正確引數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 傳遞至方法的 `format` 字串引數，例如 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 或 <xref:System.String.Format%2A?displayProperty=fullName>，不包含對應至每個物件引數的格式項目，反之亦然。  
  
## 規則描述  
 一些方法 \(例如 <xref:System.Console.WriteLine%2A>、<xref:System.Console.Write%2A> 和 <xref:System.String.Format%2A>\) 的引數是由後接幾個 <xref:System.Object?displayProperty=fullName> 執行個體的格式字串所組成。  格式字串是由文字和內嵌的項目格式所組成，形式為 {index\[,alignment\]\[:formatString\]}。'index' 是以零起始的整數，會指出需要格式化的物件。  如果物件在格式字串中沒有對應的索引，將會忽略物件。  如果由 'index' 指定的物件不存在，會在執行階段擲回 <xref:System.FormatException?displayProperty=fullName>。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請對每個物件引數提供項目格式，並對每個項目格式提供物件引數。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列範例會顯示規則的兩個違規情形。  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]