---
title: "PROFILE_CURRENTID | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PROFILE_CURRENTID"
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在對 NameProfile、StartProfile、StopProfile、SuspendProfile 和 ResumeProfile 函式的呼叫中，PROFILE\_CURRENTID 會傳回執行緒 ID 或處理序 ID 的虛擬語彙基元 \(Token\)。  使用它會造成函式在目前的執行緒或處理序上作業，而非在特別指定的執行緒或處理序上作業。  
  
## 範例  
 PROFILE\_CURRENTID 於 VSPerf.h 中定義如下：  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## 範例  
 下列範例將說明 PROFILE\_CURRENTID。  此範例使用 PROFILE\_CURRENTID 做為參數，來識別 [StartProfile](../profiling/startprofile.md) 函式呼叫中的目前執行緒。  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 請參閱  
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)