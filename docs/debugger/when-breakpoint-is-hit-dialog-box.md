---
title: "叫用中斷點時對話方塊 | Microsoft Docs"
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
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 叫用中斷點時對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

透過這個對話方塊，您可以自訂叫用中斷點時所發生的動作。  
  
## UIElement 清單  
 **列印訊息**  
 使用 DebuggerDisplay 語法列印訊息。  如需詳細資訊，請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。  
  
 這個文字方塊也支援特殊關鍵字 \(例如 $ADDRESS\)，這些關鍵字可自己使用，或在 DebuggerDisplay 運算式的大括號內。  對話方塊上會列出可用的關鍵字。  
  
 **繼續執行**  
 只有在選取 \[**列印訊息**\] 時才會啟用這個控制項。  選取這個控制項時，您可以將中斷點當做追蹤點使用以追蹤程式執行，而不是在到達位置時中斷。  
  
## 請參閱  
 [使用中斷點](../debugger/using-breakpoints.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)