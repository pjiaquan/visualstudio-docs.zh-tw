---
title: "報告巨集 | Microsoft Docs"
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
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn 巨集"
  - "_RPTn 巨集"
  - "CRT, 報告巨集"
  - "偵錯 [CRT], 報告巨集"
  - "巨集, CRT 報告巨集"
  - "巨集, 偵錯工具"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 報告巨集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在您偵錯時，可以使用在 CRTDBG.H 裡定義的 **\_RPTn** 和 **\_RPTFn** 巨集，來取代 `printf` 陳述式的使用。  如果沒有定義 **\_DEBUG**，這些巨集便會自動地消失在您的發行組建裡，因此不需要在 **\#ifdef** 裡包含它們。  
  
|巨集|說明|  
|--------|--------|  
|**\_RPT0**、**\_RPT1**、**\_RPT2**、**\_RPT3**、**\_RPT4**|輸出訊息字串和零至四個引數。  從 \_RPT1 到 **\_RPT4**，訊息字串做為引數的 printf 樣式格式字串。|  
|**\_RPTF0**、**\_RPTF1**、**\_RPTF2**、**\_RPTF4**|與 **\_RPTn** 相同，但是這些巨集也會輸出巨集所在位置的檔名和行號。|  
  
 參考下列範例：  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 這段程式碼會將 `someVar` 和 `otherVar` 的值輸出至 **stdout**。  您可以使用下列的 `_RPTF2` 呼叫來報告這些相同的值，此外，還有檔名和行號：  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 如果您發現特定應用程式需要的偵錯報告是 C 執行階段程式庫提供的巨集所沒有的，您可以撰寫特別設計的巨集來符合您自己的需要。  例如，您可以在其中一個標頭檔案中，包含像下面這段用來定義名為 **ALERT\_IF2** 巨集的程式碼：  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 一個 **ALERT\_IF2** 呼叫可以執行本主題開始的所有 **printf** 程式碼的函式：  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 因為自訂巨集可以很容易地變更為報告較多或較少資訊至不同的目的端 \(取決於哪一種比較方便\)，當您的偵錯需求不同時，這種方法特別有用。  
  
## 請參閱  
 [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)