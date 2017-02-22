---
title: "IDiaEnumFrameData::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData::Clone 方法"
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立列舉值，包含目前的列舉值的列舉型別狀態。  
  
## 語法  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### 參數  
 ppenum  
 \[\] out傳回[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)物件，包含列舉值已經存在。  圖文框的資料不重複，將列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)