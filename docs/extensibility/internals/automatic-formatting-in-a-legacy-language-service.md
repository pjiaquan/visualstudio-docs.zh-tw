---
title: "自動格式化在舊版語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務，自動格式設定"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 自動格式化在舊版語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用自動格式設定，語言服務自動插入程式碼片段時，則使用者可以在此輸入已知的程式碼建構一開始。  
  
## 自動格式設定的行為  
 比方說，當您輸入`if`、 語言服務會自動插入對稱的括號，或如果您按下 ENTER 鍵，語言服務強制將插入點在新行至適當的縮排層級，取決於是否前一行開啟新的範圍。  
  
 接下來的語言服務所用的命令篩選條件也可以用於自動格式設定。  您也可以突出對稱的括號，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>。  
  
## 請參閱  
 [開發語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)