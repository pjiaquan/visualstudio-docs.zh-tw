---
title: "如何：安裝視覺化檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, 視覺化檢視"
  - "視覺化檢視, 安裝"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：安裝視覺化檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。  安裝視覺化檢視的程序很簡單。  
  
> [!NOTE]
>  在**市集**應用程式中，只支援標準文字、HTML、XML 及 JSON 視覺化檢視。  不支援自訂 \(使用者建立的\) 視覺化檢視。  
  
### 安裝視覺化檢視  
  
1.  找出包含您已建置之視覺化檢視的 DLL。  
  
2.  將該 DLL 複製至下列其中一個位置：  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  如果要使用 Managed 視覺化檢視進行遠端偵錯，請將 DLL 複製到遠端電腦上的相同路徑中。  
  
4.  重新啟動偵錯工作階段。  
  
## 請參閱  
 [視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [如何：撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)