---
title: "複製 (程式設計擷取) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 複製 (程式設計擷取)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將作用中的圖形記錄 \(.vsglog\) 檔案複製到新檔案內。  
  
## 語法  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### 參數  
 `szNewVSGLog`  
 新的圖形記錄檔的檔案名稱。  
  
## 備註  
 若要複製圖形資訊至新的檔案，您必須取得某些圖形資訊；否則，就不會發生任何動作。