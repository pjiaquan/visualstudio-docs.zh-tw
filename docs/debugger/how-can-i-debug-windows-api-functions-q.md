---
title: "如何偵錯 Windows API 函式？ | Microsoft Docs"
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
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, 偵錯"
  - "偵錯 [C++], Windows API 函式"
  - "NT 符號和偵錯 Windows API 函式"
  - "Windows API 函式, 偵錯"
  - "Windows 應用程式開發介面, 偵錯 API 函式"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何偵錯 Windows API 函式？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果要偵錯已載入 NT 符號的 Windows API 函式，必須進行下列步驟。  
  
### 若要在含載入之 NT 符號的 Windows API 函式上設定中斷點  
  
-   輸入加上函式所在 DLL 名稱的函式名稱。  在 32 位元程式碼中，請使用函式名稱的裝飾形式。  例如，若要在 **MessageBeep** 上設定中斷點，您必須輸入下列程式碼。  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     若要取得裝飾名稱，請參閱[Viewing Decorated Names](http://msdn.microsoft.com/zh-tw/f79e2717-a4db-4d12-a689-69830cce2be0)。  
  
## 請參閱  
 [機器碼偵錯 FAQ](../debugger/debugging-native-code-faqs.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)