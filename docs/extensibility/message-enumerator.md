---
title: "訊息的列舉值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "訊息的列舉值"
  - "原始檔控制外掛程式，訊息的列舉型別"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 訊息的列舉值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列旗標會用於 `TEXTOUTPROC` 函式，也就是 IDE 提供呼叫時的回呼函式 [SccOpenProject](../extensibility/sccopenproject-function.md) \(請參閱 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 的回呼函式的詳細資訊\)。  
  
 如果 IDE 已要求取消此程序，它可能會收到的其中一個 \[取消\] 訊息。 在此情況下，原始檔控制外掛程式用 `SCC_MSG_STARTCANCEL` 要求顯示 IDE **取消** \] 按鈕。 在此之後，可能會傳送一般訊息的任何設定。 如果任何這些傳回 `SCC_MSG_RTN_CANCEL`, ，則會結束作業並傳回外掛程式。 外掛程式也會輪詢 `SCC_MSG_DOCANCEL` 定期來判斷是否使用者已取消作業。 當所有作業完成都之後，或如果使用者已經取消，外掛程式會傳送 `SCC_MSG_STOPCANCEL`。`SCC_MSG_INFO`, ，SCC\_MSG\_WARNING，和 SCC\_MSG\_ERROR 類型會用於捲動郵件清單中顯示的訊息。`SCC_MSG_STATUS` 是一種特殊類型，表示文字應出現在狀態列或暫存的顯示區域中。 它不會永遠在清單中。  
  
## 語法  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## 成員  
 SCC\_MSG\_RTN\_CANCEL  
 傳回表示取消回呼。  
  
 SCC\_MSG\_RTN\_OK  
 傳回從回呼，以繼續。  
  
 SCC\_MSG\_INFO  
 是參考訊息。  
  
 SCC\_MSG\_WARNING  
 這是一個警告訊息。  
  
 SCC\_MSG\_ERROR  
 這是一個錯誤訊息。  
  
 SCC\_MSG\_STATUS  
 訊息是用狀態列。  
  
 SCC\_MSG\_DOCANCEL  
 任何文字。傳回 IDE `SCC_MSG_RTN_OK` 或 `SCC_MSG_RTN_CANCEL`。  
  
 SCC\_MSG\_STARTCANCEL  
 啟動 \[取消\] 迴圈。  
  
 SCC\_MSG\_STOPCANCEL  
 取消迴圈就會停止。  
  
## 請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)