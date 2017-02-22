---
title: "DA0506：為進行程式碼剖析的處理序所配置的最大私用位元組 | Microsoft Docs"
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
  - "vs.performance.rules.DA0506"
  - "vs.performance.DA0506"
  - "vs.performance.506"
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0506：為進行程式碼剖析的處理序所配置的最大私用位元組
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0506|  
|分類|資源監視|  
|程式碼剖析方法|全部|  
|Message|蒐集這項資訊僅供參考之用。  Process Private Bytes 計數器會測量您要進行程式碼剖析之處理序所配置的虛擬記憶體。  回報的值就是在所有測量間隔中觀察到的最大值。|  
|規則型別|資訊|  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行程式碼剖析時，必須至少收集 10 個範本才能觸發此規則。  
  
## 規則描述  
 這個訊息回報處理序目前已配置的最大虛擬記憶體量 \(私用位元組，以位元組為單位\)。  私用位元組代表由處理序所配置而且只能供在處理序內部執行之執行緒存取的虛擬記憶體位置。  
  
 對於在 32 位元電腦上執行的 32 位元處理序，處理序位址空間私用部分的上限為 2 GB。  使用 [\/ 3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini 參數， 32 位元處理序可以取得多達 3 GB 的虛擬記憶體。  在 64 位元電腦上執行的 32 位元處理序可以取得多達 4 GB 的私用虛擬記憶體。  
  
 在 64 位元電腦上執行的 64 位元處理序可以取得多達 8 TB 的私用虛擬記憶體。  
  
 回報的值是進行程式碼剖析之處理序處於作用中狀態的所有測量間隔期間的最大值。  
  
 如需處理序位址空間的詳細資訊，請參閱＜Windows 記憶體管理＞文件中的[虛擬位址空間](http://go.microsoft.com/fwlink/?LinkId=177832) \(英文\)。  
  
## 如何使用規則資料  
 使用回報值可以比較程式之不同版本或組建間的效能，或了解應用程式在不同程式碼剖析情節下的效能。  
  
 接近處理序位址空間架構上限的處理序私用位元組最大值可能會導致記憶體不足例外狀況。  如需詳細資訊，請參閱 MSDN Magazine 中 [調查的記憶體問題](http://go.microsoft.com/fwlink/?LinkID=177833)。