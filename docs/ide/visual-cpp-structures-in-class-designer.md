---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[類別設計工具\] 支援 C\+\+ 結構，這些結構是以 `struct` 關鍵字進行宣告。  下列為範例：  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 如需使用 `struct` 型別的詳細資訊，請參閱 [struct](/visual-cpp/cpp/struct-cpp)。  
  
 在類别圖表中的 C\+\+ 結構圖案，其外觀和作用與類別圖案大致相同，除了標籤 \(Label\) 顯示 \[**Struct**\]，並且具有方的邊角，而非圓的邊角。  
  
|程式碼項目|類別設計工具檢視|  
|-----------|--------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|  
  
## 請參閱  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [類別和結構](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)