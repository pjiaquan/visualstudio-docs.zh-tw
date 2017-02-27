---
title: "CommentMarkAtProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`CommentMarkAtProfile` 方法會在 .vsp 檔中插入時間戳記值、數字標記和註解字串。  時間戳記值可以用來同步處理外部事件。  若要插入標記和註解，包含 CommentMarkAtProfile 函式之執行緒的剖析必須是 ON。  
  
## 語法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### 參數  
 `dnTimestamp`  
  
 代表時間戳記值的 64 位元整數。  
  
 `lMarker`  
  
 要插入的數字標記，  標記必須大於或等於 0 \(零\)。  
  
 `szComment`  
  
 要插入的文字字串指標，  字串必須少於 256 個字元，其中包含 NULL 結束字元。  
  
## 屬性值\/傳回值  
 此函式會使用 **PROFILE\_COMMAND\_STATUS** 列舉型別來表示成功或失敗。  傳回值可以是下列其中之一：  
  
|Enumerator|描述|  
|----------------|--------|  
|MARK\_ERROR\_MARKER\_RESERVED|該參數小於或等於 0。  會保留這些值。  標記和註解都不會記錄。|  
|MARK\_ERROR\_MODE\_NEVER|當呼叫函式時，分析模式是設定為 NEVER。  標記和註解都不會記錄。|  
|MARK\_ERROR\_MODE\_OFF|當呼叫函式時，分析模式是設定為 OFF。  標記和註解都不會記錄。|  
|MARK\_ERROR\_NO\_SUPPORT|此內容不支援任何標記。  標記和註解都不會記錄。|  
|MARK\_ERROR\_OUTOFMEMORY|無法使用記憶體記錄事件。  標記和註解都不會記錄。|  
|MARK\_TEXTTOOLONG|字串超過最大值 256 字元，  註解字串遭截斷，且已記錄標記和註解。|  
|MARK\_OK|傳回 MARK\_OK 是表示成功。|  
  
## 備註  
 當以 Mark 命令或 API 函式 \(CommentMarkAtProfile、CommentMarkProfile 或 MarkProfile\) 插入標記和註解時，包含標記設定檔函式之執行緒的設定檔狀態必須為開啟狀態。  設定檔標記屬於全域範圍。  例如，在一個執行緒中插入的設定檔標記可用來標記 .vsp 檔中任何執行緒內的資料區段之開頭或結尾。  
  
> [!IMPORTANT]
>  CommentMarkAtProfile 方法應該只和檢測一起使用。  
  
## .NET Framework 對等用法  
 Microsoft.VisualStudio.Profiler.dll  
  
## 功能資訊  
  
|||  
|-|-|  
|**Header**|包含 VSPerf.h|  
|**程式庫**|使用 VSPerf.lib|  
|**Unicode**|實作為 CommentMarkAtProfileW \(Unicode\) 和 CommentMarkAtProfileA \(ANSI\)。|  
  
## 範例  
 下列程式碼將說明 CommentMarkAtProfile 泛型函式呼叫的用法。  此範例會假設使用 Win32 字串巨集和 ANSI 的編譯器設定來判斷程式碼是否呼叫啟用 ANSI 的函式。  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 請參閱  
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)