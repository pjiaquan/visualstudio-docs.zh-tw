---
title: "並行視覺化檢視 SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 並行視覺化檢視 SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以透過使用"並行視覺化檢視 SDK 顯示"取得視覺化檢視的其他資訊來偵測您的原始程式碼。  您可以結合其他資訊階段和程式碼中的事件。  這些額外的視覺化稱為x  *標記*。如需入門逐步解說，請參閱 [介紹並行視覺化檢視 SDK](http://go.microsoft.com/fwlink/?LinkId=235405)。  
  
## 屬性  
 旗標、間距和訊息都有兩個屬性:分類和重要性。  在 [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊中，您可以使用這些屬性篩選已顯示的一組旗標。  此外，這些屬性會影響資料標記的視覺化表示。  例如，旗標的大小用於表示重要性。  此外，色彩來標示分類。  
  
## 基本使用方式  
 "並行視覺化檢視"會公開許多您可用來產生標記的預設提供者。  提供者已與並行視覺化檢視一起註冊，而且您不需要在 UI 中執行其他標記工作。  
  
### Visual Basic 和 C\#  
 在 C\# ， Visual Basic 和其他 Managed 程式碼中，藉由呼叫 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>使用預設提供者。  它會公開所產生的標記四個函式: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>、 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>、 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>和 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>。  這些函式的多載，視您要使用屬性的預設值。最簡單的多載指定事件的說明字串參數。  這個描述"並行視覺化檢視" 的報表會顯示。  
  
##### 若要將 SDK 支援加入至 C\# 或 Visual Basic 專案  
  
1.  在功能表列上，選取 \[**分析**\]， \[**並行視覺化檢視**\]， \[**將 SDK 加入專案**\]。  
  
2.  選取您要存取的 SDK， 然後選取 \[**將 SDK 加入選取的專案**\] 按鈕的專案。  
  
3.  加入匯入或使用陳述式至您的程式碼。  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 在 C\+\+ 中，建立 [marker\_series 類別](../profiling/marker-series-class.md) 物件並使用它來呼叫函式。`marker_series` 類別公開產生的標記、 [marker\_series::write\_flag 方法](../profiling/marker-series-write-flag-method.md)、 [marker\_series::write\_message 方法](../profiling/marker-series-write-message-method.md)和 [marker\_series::write\_alert 方法](../profiling/marker-series-write-alert-method.md)三個功能。  
  
##### 若要將 SDK 支援加入至 C\+\+ 或 C 專案  
  
1.  在功能表列上，選取 \[**分析**\]， \[**並行視覺化檢視**\]， \[**將 SDK 加入專案**\]。  
  
2.  選取您要存取的 SDK， 然後選取 \[**將 SDK 加入選取的專案**\] 按鈕的專案。  
  
3.  對於 C\+\+ ，包含 `cvmarkersobj.h`。  對於 C，包含 `cvmarkers.h`。  
  
4.  若要加入使用陳述式加入至您的程式碼。  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  建立新的 `marker_series` 物件，然後將 `span` 物件傳遞給它。  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## 自訂使用方式  
 針對進階案例中，並行視覺化檢視SDK以公開多個控制項。兩個主要概念與其他進階案例:標記提供者和標記系列。  標記提供者是不同的 ETW 提供者 \(每一個都有不同的 GUID\)。  標記系列是由提供者所產生的事件序列的通道。  您可以使用它們來組織由標記提供者所產生的活動。  
  
#### 若要在 C\# 或 Visual Basic 專案中使用新的標記提供者  
  
1.  建立 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> 物件。建構函式接受 GUID。  
  
2.  若要註冊提供者，請開啟 \[並行視覺化檢視\] [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊。選取 \[**標記**\] 索引標籤然後選取 \[**加入新提供者**\] 按鈕。  在 [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊中，輸入用來建立提供者和提供者描述的 GUID。  
  
#### 若要在 C\+\+或 C專案使用新的標記提供者  
  
1.  使用 `CvInitProvider` 函式初始化 PCV\_PROVIDER。建構函式接受 GUID\*和 PCV\_PROVIDER\*。  
  
2.  若要註冊提供者，請開啟 [進階設定](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 對話方塊。選取 \[**標記**\] 索引標籤然後選取 \[**加入新提供者**\] 按鈕。  在這個對話方塊中，輸入用來建立提供者和提供者描述的 GUID。  
  
#### 若要在 C\# 或 Visual Basic 專案使用標記數列  
  
1.  您可以使用 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> 物件，則會使用新的 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>，請先建立它，然後再產生標記事件直接從新系列。  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### 若要在 C\+\+專案使用標記數列  
  
1.  建立 `marker_series` 物件。您可以從這個新一系列產生事件。  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### 若要在C專案使用標記數列  
  
1.  使用 `CvCreateMarkerSeries` 函式建立 PCV\_MARKERSERIES。  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)|描述 C\+\+ 的並行視覺化檢視應用程式開發介面。|  
|[C 程式庫參考](../profiling/c-library-reference.md)|描述 C 的並行視覺化檢視應用程式開發介面。|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|描述 Managed 程式碼的並行視覺化檢視應用程式開發介面。|  
|[並行視覺化檢視](../profiling/concurrency-visualizer.md)|針對使用並行方法並包含執行緒執行資料的程式碼剖析資料檔案，提供其檢視和報告的參考資訊。|