---
title: "如何：序列化符號資訊 | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "程式碼剖析工具，序列化符號資訊"
  - "效能工具，序列化符號資訊"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：序列化符號資訊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以將分析應用程式所必要的符號予以序列化。  符號序列化會將符號加入到 .vsp 檔中。  藉由將符號加入到 .vsp 檔中，其他人不必存取原始符號，就可以分析效能報表。  如果符號未序列化，您必須擁有原始檢測的 .exe 和 .pdb 檔，才能分析 .vsp 檔。  
  
### 自動序列化符號資訊  
  
1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
     \[**選項**\] 對話方塊隨即出現。  
  
2.  按一下 \[**效能工具**\]。  
  
3.  在 \[**一般設定**\] 下，選取 \[**自動序列化符號資訊**\]。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/zh-tw/0340ddde-caf4-48ac-8af3-d15dcdade556)