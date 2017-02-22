---
title: "呼叫堆疊視窗內的混合程式碼和遺失的資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
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
helpviewer_keywords: 
  - "Managed 程式碼, 逐步執行"
  - "[呼叫堆疊] 視窗, 混合模式偵錯"
  - "[呼叫堆疊] 視窗, 疑難排解"
  - "原生框架"
  - "Managed 呼叫堆疊"
  - "混合模式偵錯, 呼叫堆疊"
  - "跳離 , Managed 程式碼"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 呼叫堆疊視窗內的混合程式碼和遺失的資訊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

因為 Managed 和機器碼呼叫堆疊之間的差異，當程式碼類型混合時，偵錯工具則無法永遠顯示完整的呼叫堆疊。  當機器碼呼叫 Managed 程式碼時，您會在 \[**呼叫堆疊**\] 視窗內看到下列差異：  
  
-   Managed 程式碼正上方的原生框架可能會從 \[**呼叫堆疊**\] 視窗消失。  如需詳細資訊，請參閱 [如何：在原生框架遺失於呼叫堆疊顯示時跳離 Managed 程式碼](../Topic/How%20to:%20Step%20out%20of%20Managed%20Code%20when%20Native%20Frames%20are%20Missing%20from%20the%20Call%20Stack%20Window.md)。  
  
-   針對啟動於偵錯工具外部的混合模式應用程式，\[**呼叫堆疊**\] 視窗只會顯示 Managed 程式碼，並且看不到任一個原生框架。  
  
 這兩個狀況都相當少見。  在大多數呼叫 Managed 程式碼的原生呼叫中，呼叫堆疊看起來都是正確的。  
  
## 請參閱  
 [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)