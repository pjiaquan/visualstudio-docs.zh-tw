---
title: "如何：尋找程式損毀時所在的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, DLL 損毀"
  - "偵錯 [Visual Studio], DLL 損毀"
  - "DLL, 載入順序"
  - "錯誤 [偵錯工具], DLL 損毀"
  - "模組清單對話方塊"
  - "模組視窗"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：尋找程式損毀時所在的 DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[工具\] 功能表中選取 \[匯入和匯出設定\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。  如果您遇到的損毀是由程式以外的 DLL 所致，您可以使用 \[**模組**\] 視窗來辨識其位置。  
  
### 若要使用模組視窗來尋找毀損之處  
  
1.  記下發生毀損的位址。  
  
2.  在 \[**偵錯**\] 功能表上選擇 \[**Windows**\]，然後按一下 \[**模組**\]。  
  
3.  在 \[**模組**\] 視窗中尋找出 \[**位址**\] 欄位。  您可能需要使用捲軸才能看到它。  
  
4.  按一下 \[**位址**\] 按鈕 \(在該欄位的最上方\) 以便依位址排序 DLL。  
  
5.  瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。  
  
6.  檢視 \[**名稱**\] 和 \[**路徑**\] 欄位以查看此 DLL 名稱和路徑。  
  
## 請參閱  
 [如何：偵錯原生 DLL](../Topic/How%20to:%20Debug%20Native%20DLLs.md)   
 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)