---
title: "CvCreateMarkerSeriesWithCodePageA 函式 | Microsoft Docs"
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
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA 方法"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateMarkerSeriesWithCodePageA 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立指定之提供者和指定的字碼頁的正負號系列。  這個函式可以用來簽署 API ANSI 函式寫出文字明確指定字碼頁。  以防在追蹤不同地區設定和語言的不同，電腦會擷取並進行分析設定字碼頁可能會很有用。  預設會使用 GetACP\(\) 函式傳回的字碼頁。  
  
## 語法  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### 參數  
 `pProvider`  
 CvInitProvider 先前初始化之提供者的物件。  不可為 NULL 。  
  
 `pSeriesName`  
 標記的系列名稱。  不可以是 null，但允許空白字串。  
  
 `nTextCodePage`  
 無效的字碼頁。  
  
 `ppMarkerSeries`  
 要儲存的資料標記系列內容輸出變數的位址。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當一系列標記已成功建立或以防萬一有任何錯誤碼錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)