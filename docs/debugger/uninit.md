---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

完成圖形記錄檔並關閉，然後在應用程式有效地記錄圖形資訊後，釋放使用的資源。  
  
## 語法  
  
```cpp  
void UnInit();  
```  
  
## 備註  
 在終結 `VsgDbg` 類別的執行個體時，會自動呼叫 `UnInit`。  如果 `VsgDbg` 執行個體未啟用記錄圖形資訊，這就沒有任何作用。  
  
 在 `VsgDbg` 類別執行個體上呼叫 `UnInit` 之後，可以透過呼叫 `Init`、`UnInit` 來分別創建、終結新的圖形記錄檔。  當您想要使用相同的 `VsgDbg` 執行個體來建立多個獨立圖形記錄檔時，您可以不斷重複此步驟。  
  
## 請參閱  
 [Init](../debugger/init.md)