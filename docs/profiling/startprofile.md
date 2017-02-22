---
title: "StartProfile | Microsoft Docs"
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
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`StartProfile` 函式會將指定之分析層級的計數器設為 1 \(on\)。  
  
## 語法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### 參數  
 `Level`  
  
 表示可套用效能資料集合的設定檔層級。  下列 **PROFILE\_CONTROL\_LEVEL** 列舉程式可用來表示可套用效能資料集合之三個層級中的一個層級：  
  
|Enumerator|描述|  
|----------------|--------|  
|PROFILE\_GLOBALLEVEL|全域層級設定會影響程式碼剖析回合中的所有處理序和執行緒。|  
|PROFILE\_PROCESSLEVEL|處理序層級設定會影響屬於指定之處理序的所有執行緒。|  
|PROFILE\_THREADLEVEL|執行緒分析層級設定會影響指定的執行緒。|  
  
 `dwId`  
  
 由系統產生的處理序或執行緒識別項。  
  
## 屬性值\/傳回值  
 此函式會使用 **PROFILE\_COMMAND\_STATUS** 列舉型別來表示成功或失敗。  傳回值可以是下列其中之一：  
  
|Enumerator|描述|  
|----------------|--------|  
|PROFILE\_ERROR\_ID\_NOEXIST|分析項目 ID 不存在。|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|所指定的分析層級不存在。|  
|PROFILE\_ERROR\_MODE\_NEVER|當呼叫函式時，分析模式是設定為 NEVER。|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|尚未實作分析函式呼叫、分析層級，或呼叫與層級的組合。|  
|PROFILE\_OK|呼叫成功。|  
  
## 備註  
 StartProfile 和 StopProfile 會控制分析層級的開始\/停止狀態。  Start\/Stop 的預設值為 1。  可在登錄中變更初始值。  每個對 StartProfile 的呼叫會將開始\/停止設定為 1；而每個對 StopProfile 的呼叫會將開始\/停止設定為 0。  
  
 當開始\/停止大於 0 時，該層級的開始\/停止狀態會為 ON。  當它小於或等於 0 時，開始\/停止狀態則為 OFF。  
  
 當 Start\/Stop 狀態和 Suspend\/Resume 狀態兩者都為 ON 時，此層級的分析狀態就會是 ON。  對於要分析的執行緒，該執行緒的全域、處理序和執行緒層級狀態都必須為 ON。  
  
## .NET Framework 對等用法  
 Microsoft.VisualStudio.Profiler.dll  
  
## 功能資訊  
 標頭：在 VSPerf.h 中宣告  
  
 匯入程式庫: VSPerf.lib  
  
## 範例  
 下列範例將說明 StartProfile 函式呼叫。  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
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