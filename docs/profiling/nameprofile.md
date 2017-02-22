---
title: "NameProfile | Microsoft Docs"
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
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`NameProfile` 函式會指派字串給指定的處理序或執行緒。  
  
 NameProfile API 僅適用於檢測分析。  NameProfile API 不支援取樣分析。  
  
## 語法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### 參數  
 `pszName`  
  
 分析項目的名稱。  下列情況時名稱無效 \(造成 NameProfileA 傳回 NAME\_ERROR\_INVALID\_NAME\)：  
  
-   傳入 NameProfileA 的指標是 NULL 值  
  
-   pszName 的字串資料以數字為開頭  
  
-   pszName 的字串資料包含空白  
  
-   pszName 的字串資料包含下列任何字元：,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 表示可套用效能資料集合的設定檔層級。  下列 **PROFILE\_CONTROL\_LEVEL** 值可用來表示可套用效能資料集合之三個層級中的一個層級：  
  
|Enumerator|說明|  
|----------------|--------|  
|PROFILE\_GLOBALLEVEL|全域層級設定會影響程式碼剖析回合中的所有處理序和執行緒。|  
|PROFILE\_PROCESSLEVEL|處理序層級設定會影響屬於指定之處理序的一部分的所有執行緒。|  
|PROFILE\_THREADLEVEL|執行緒分析層級設定會影響指定的執行緒。|  
  
 `dwId`  
  
 分析層級識別項。  使用由系統產生的處理序或執行緒識別項。  
  
## 屬性值\/傳回值  
 此函式會使用 **PROFILE\_COMMAND\_STATUS** 列舉型別來表示成功或失敗。  傳回值可以是下列其中之一：  
  
|Enumerator|說明|  
|----------------|--------|  
|NAME\_ERROR\_ID\_NOEXIST|所指定的分析項目不存在。|  
|NAME\_ERROR\_INVALID\_NAME|名稱無效。|  
|NAME\_ERROR\_LEVEL\_NOEXIST|所指定的分析層級不存在。|  
|NAME\_ERROR\_NO\_SUPPORT|不支援指定的作業。|  
|NAME\_ERROR\_OUTOFMEMORY|無法使用記憶體記錄事件。|  
|NAME\_ERROR\_REDEFINITION|已經指派名稱給程式碼剖析項目，  此函式中的名稱會被忽略。|  
|NAME\_ERROR\_TEXTTRUNCATED|名稱文字超過 32 個字元，其中包含 null 字元，因此已遭截斷。|  
|NAME\_OK|已成功註冊名稱。|  
  
## 備註  
 只能為每個處理序或執行緒指定一個名稱。  在為分析項目命名後，會忽略後續對該項目的 NameProfile 呼叫。  
  
 如果不同的執行緒或處理序具有相同的名稱，報告將會包含該層級中具有該名稱的所有項目的資料。  
  
 如果您指定目前的處理序或執行緒以外的處理序或執行緒，就必須確定在您為它命名以前，它已經初始化並開始執行。  否則，NameProfile 方法會失敗。  
  
> [!IMPORTANT]
>  CreateProcess\(\) 和 CreateThread\(\) API 函式都可在執行緒或處理序初始化完成之前傳回。  
  
## .NET Framework 對等用法  
 Microsoft.VisualStudio.Profiler.dll  
  
## 功能資訊  
  
|||  
|-|-|  
|**Header**|包含 VSPerf.h|  
|**程式庫**|使用 VSPerf.lib|  
|**Unicode**|實作為 `NameProfileW` \(Unicode\) 和 `NameProfileA` \(ANSI\)。|  
  
## 範例  
 下列程式碼將說明 NameProfile 函式呼叫。  此範例會假設使用 Win32 字串巨集和 ANSI 的編譯器設定來判斷程式碼是否呼叫啟用 ANSI 的函式。  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 請參閱  
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)