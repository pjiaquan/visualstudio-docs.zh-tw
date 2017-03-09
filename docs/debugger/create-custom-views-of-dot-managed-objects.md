---
title: "顯示自訂資料類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat 檔案"
  - "自訂資料類型"
  - "資料類型 [C#], 自訂"
  - "偵錯工具, 展開資料類型"
  - "Managed 程式碼, 自訂資料類型"
  - "mcee_cs.dat 檔案"
  - "mcee_mc.dat 檔案"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 顯示自訂資料類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以自訂 Visual Studio 在偵錯工具變數視窗中顯示資料型別的方式。  
  
## 屬性  
 在 C\# 和 Visual Basic 中，您可以使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 加入自訂資料的擴充功能。  
  
 在 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 程式碼中，Visual Basic 不支援 DebuggerBrowsable 屬性。  最新版的 .NET Framework 中已移除此限制。  
  
## 視覺化工具  
 您可以撰寫視覺化檢視以顯示任何 Managed 資料型別。  如需詳細資訊，請參閱 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)。  
  
## 機器碼  
 針對機器碼，您可以將自訂資料型別擴充功能加入至 autoexp.dat 檔，其位於 Program Files\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger 目錄中。  如何撰寫 `autoexp` 規則的指令位於檔案本身中。  
  
> [!CAUTION]
>  這個檔案的結構和 autoexp 規則語法可能因 Visual Studio 發行版本不同而有所差異。  
  
 您也可以透過撰寫運算式評估工具增益集來自訂原生型別檢視。  如需詳細資訊，請參閱 [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/zh-tw/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)。  
  
## 請參閱  
 [使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)   
 [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)