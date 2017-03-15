---
title: "DA0013：String.Split 或 String.Substring 的用量高 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DAAvoidStringSubstr"
  - "vs.performance.DA0013"
  - "vs.performance.rules.DA0013"
helpviewer_keywords: 
  - "vs.performance.13"
  - "vs.performance.rules.DA0013"
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0013：String.Split 或 String.Substring 的用量高
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0013|  
|分類|.NET Framework 使用指引|  
|程式碼剖析方法|取樣|  
|訊息|考慮減少使用 String.Split 和 String.Substring 函式。|  
|規則型別|警告|  
  
## 原因  
 System.String.Split 或 System.String.Substring 方法的呼叫佔有程式碼剖析資料的一大部分。  如果您要測試字串中是否存在子字串，請考慮使用 System.String.IndexOf 或 System.String.IndexOfAny。  
  
## 規則描述  
 Split 方法會在 String 物件上作業，並傳回 String 的新陣列，其中包含原始字串的子字串。  此函式會為傳回的陣列物件配置記憶體，並會為它找到的每個陣列元素配置新的 String 物件。  同樣的，Substr 方法會在 String 物件上作業，然後傳回新的 String，其值相當於所要求的子字串。  
  
 如果管理記憶體配置在您的應用程式中極為重要，請考慮使用 String.Split 和 String.Substr 方法的替代方案。  例如，您可以使用 IndexOf 或 IndexOfAny 方法，來尋找字元字串內的特定子字串，而不需要建立 String 類別的新執行個體。  
  
## 如何調查警告  
 按兩下 \[錯誤清單\] 視窗中的訊息，即可巡覽至取樣程式碼剖析資料的[函式詳細資料檢視](../profiling/function-details-view.md)。  檢查呼叫函式，以找出最常使用 System.String.Split 或 System.String.Substr 方法之程式的區段。  如果可能的話，使用 IndexOf 或 IndexOfAny 方法來尋找字元字串內的特定子字串，而不建立 String 類別的新執行個體。