---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`CommentMarkProfile` 函式會在 .vsp 檔中插入數字標記和文字字串。  若要插入標記和註解，包含 `CommentMarkProfile` 函式之執行緒的剖析必須是 ON。  
  
## 語法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### 參數  
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
 當以 VSInstr Mark 命令或以函式 \(CommentMarkAtProfile、CommentMarkProfile 或 MarkProfile\) 插入標記和註解時，包含標記設定檔函式之執行緒的剖析狀態必須為開啟狀態。  
  
 設定檔標記屬於全域範圍。  例如，在一個執行緒中插入的設定檔標記可用來標記 .vsp 檔中任何執行緒內的資料區段之開頭或結尾。  
  
> [!IMPORTANT]
>  CommentMarkProfile 方法只能和檢測一起使用。  
  
## .NET Framework 對等用法  
 Microsoft.VisualStudio.Profiler.dll  
  
## 功能資訊  
  
|||  
|-|-|  
|**Header**|包含 VSPerf.h|  
|**程式庫**|使用 VSPerf.lib|  
|**Unicode**|實作為 `CommentMarkProfileW` \(Unicode\) 和 `CommentMarkProfileA` \(ANSI\)。|  
  
## 範例  
 下列程式碼將說明 CommentMarkProfile 函式呼叫。  此範例會假設使用 Win32 字串巨集和 Unicode 編譯器設定來判斷程式碼是否呼叫 [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)] 函式呼叫。  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 請參閱  
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)