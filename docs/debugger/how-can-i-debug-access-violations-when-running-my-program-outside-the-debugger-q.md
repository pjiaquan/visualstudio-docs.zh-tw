---
title: "在偵錯工具外執行我的程式時，如何偵錯存取違規？ | Microsoft Docs"
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
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "存取違規偵錯"
  - "偵錯 [Visual Studio], 存取違規"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在偵錯工具外執行我的程式時，如何偵錯存取違規？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 問題說明  
 我的程式在 Visual Studio 環境裡執行正常，但是當我以 Windows 作業系統獨立執行它時，它會產生存取違規。  我該如何偵錯這個問題？  
  
## 方案  
 設定 [Just\-in\-time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)選項並獨立執行您的程式，直到發生存取違規為止。  接著，在 \[存取違規\] 對話方塊裡，您可以按一下 \[取消\] 來啟動偵錯工具。  
  
 請參閱知識庫 \(Knowledge Base\) 文件 Q133174「How to Locate Where a General Protection \(GP\) Fault Occurs」。您可以在 MSDN Library CD 上找到知識庫文件，或者可以搜尋 [http:\/\/support.microsoft.com\/](http://support.microsoft.com/)。  
  
## 請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)