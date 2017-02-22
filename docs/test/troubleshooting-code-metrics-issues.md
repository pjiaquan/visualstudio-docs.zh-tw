---
title: "程式碼度量問題疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
caps.handback.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# 程式碼度量問題疑難排解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您收集程式碼度量時，可能會遇到下列一些問題：  
  
-   [Visual Studio 2010 程式碼複雜度計算的變更](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Visual Studio 2010 程式碼複雜度計算的變更  
 相同的函式運用在下列情況時，[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中計算的程式碼複雜度度量可能與舊版 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 計算的度量不同：  
  
-   函式包含一個或多個 catch 區塊。  在舊版 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，catch 區塊不包含在計算中。  在 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 中，每個 catch 區塊的複雜度都會加入至函式複雜度。  
  
-   函式包含 switch \(在 VB 中為 Select Case\) 陳述式。  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 和舊版之間的編譯器差異可能會對包含繼續 case 的一些 switch 陳述式產生不同的 MSIL 程式碼。  
  
## 請參閱  
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)