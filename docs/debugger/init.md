---
title: "Init | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Init
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

準備圖形診斷應用程式元件有效地擷取和記錄圖形資訊至圖形記錄檔。  
  
## 語法  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### 參數  
 `vsgLogGetter`  
 可呼叫實體這類為函式，函式指標， Lambda 函式、函式物件做為參數緩衝區所組成的 `wchar_t` 和指標的長度對該緩衝區，並傳回 `void`。  當被叫用，可呼叫的實體判斷用來記錄圖形資訊的檔案名稱和寫入至指定的資料緩衝區後再傳回。  
  
## 備註  
 `Init` 函式，就會呼叫 `VsgDbg` 類別的執行個體可以指定其建構函式 `bDefaultInit` 參數建構時為 `true`;否則，在這種情況下，您可以有效地擷取和記錄圖形資訊之前，必須明確呼叫 `Init` 。  
  
 您可以藉由呼叫 `UnInit`完成和關閉使用中的圖形記錄檔，然後取得和記錄詳細圖形資訊加入至新的圖形記錄檔可以再次呼叫 `Init` 。  當您想要藉由使用相同的 `VsgDbg` 執行個體來建立多個獨立圖形記錄檔時，您可以不斷重複此步驟。  
  
## 請參閱  
 [UnInit](../debugger/init.md)