---
title: "將 EventSource 事件顯示為標記 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 將 EventSource 事件顯示為標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

並行視覺化檢視會顯示 EventSource 事件當做資料標記，然後，您可以控制項標記的顯示方式。  您可以使用 [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊以註冊 ETW 提供者 GUID，然後檢視 EventSource 標記。  並行視覺化檢視有預設慣例將 EventSource 事件表示為 [旗標標記](../profiling/flag-markers.md)、 [延伸標記](../profiling/span-markers.md)和 [訊息標記](../profiling/message-markers.md)。  您可以藉由加入自訂欄位至事件，自訂 EventSource 事件如何顯示。  如需巨集的詳細資訊，請參閱[並行視覺化檢視中的標記](../profiling/concurrency-visualizer-markers.md)。  如需應用程式事件的詳細資訊，請參閱 <xref:System.Diagnostics.Tracing>。  
  
## 預設 EventSource 事件的視覺效果  
 根據預設，並行視覺化檢視會使用下列慣例表示 EventSource 事件。  
  
### 標記類型  
  
1.  具有win:Start 或 win:Stop [Opcode](http://msdn.microsoft.com/zh-tw/d97953df-669b-4c55-b1a8-925022b339b7) 的事件，將分別視為延伸的開頭或結尾。巢狀或重疊的延伸無法顯示。  開始於一個執行緒和結尾於另一個執行緒的事件配對將無法顯示。  
  
2.  Opcode 不是win:Start 也不是win:Stop 的事件，，除非它的 [色階](http://msdn.microsoft.com/zh-tw/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR 欄位\) 是 win:Verbose 或更高，否則不會視為符號旗標。  
  
3.  在所有其他情況下，事件都視為訊息。  
  
### 重要性  
 下列資料表定義事件層級如何對應至標記重要性。  
  
|ETW 階段|並行視覺化檢視的重要性|  
|------------|-----------------|  
|Win: LogAlways|Normal|  
|win: Critical|Critical|  
|win: Error|Critical|  
|win: Warning|高|  
|win: Informational|Normal|  
|win: Verbose|低|  
|大於 win: verbose|低|  
  
### 序列名稱。  
 事件的工作名稱被使用於系列名稱。  如果事件沒有工作，序列名稱則會定義成空白。  
  
### 分類  
 如果層級是 win: Critical或 win: Erro，則分類為警示 \(\- 1\)。  否則，分類為預設值 \(0\)。  
  
### 文字  
 如果有一個事件的printf 型別的格式化文字訊息被定義，它會顯示為標記的描述。  否則，這個描述是事件的名稱和每個裝載欄位的值。  
  
## 自訂 EventSource 事件的視覺效果  
 您可以透過將適當的欄位顯示為事件來自訂 EventSource 事件，如下列章節所述。  
  
### 標記類型  
 使用 `cvType` 欄位，一個位元組，控制用來表示事件的這種標記。  cvType 可用的值:  
  
|cvType 值|產生標記的型別|  
|--------------|-------------|  
|0|Message|  
|1|延伸的開頭|  
|2|延伸的結尾。|  
|3|旗標|  
|所有其他的值|Message|  
  
### 重要性  
 您可以使用 `cvImportance` 欄位，一個位元組，控制EventSource 事件的重要性的設定值。  不過，我們建議您使用層級控制事件上所顯示的重要性。  
  
|cvImportance 值|並行視覺化檢視的重要性|  
|--------------------|-----------------|  
|0|Normal|  
|1|Critical|  
|2|高|  
|3|高|  
|4|Normal|  
|5|低|  
|所有其他的值|低|  
  
### 序列名稱。  
 使用 `cvSeries` 事件欄位， String，控制並行視覺化檢視提供給 EventSource 事件的系列名稱。  
  
### 分類  
 使用 `cvCategory` 欄位，一個位元組，控制並行視覺化檢視提供給EventSource 事件的分類。  
  
### 文字  
 使用 `cvTextW` 欄位， String，控制並行視覺化檢視提供給EventSource 事件的描述。  
  
### SpanID  
 使用 cvSpanId 欄位， int，以符合事件配對。  表示間距的每一組值\(開始\/停止事件\)必須是唯一的。  通常並行程式碼要求使用同步處理基本型別 \(例如 <xref:System.Threading.Interlocked.Exchange%2A> 以確認使用的金鑰 \(提供給 CvSpanID值\)是正確的。  
  
> [!NOTE]
>  使用 SpanID 巢狀延伸允許在相同執行緒部分重疊，但開始與結束於不同執行緒則不支援。  
  
## 請參閱  
 [並行視覺化檢視中的標記](../profiling/concurrency-visualizer-markers.md)