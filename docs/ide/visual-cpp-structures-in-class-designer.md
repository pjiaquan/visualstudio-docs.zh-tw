---
title: "類別設計工具中的 Visual C++ 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 5f15cb38d9bd9f5035f9c02ef1beaf5d19da143b
ms.lasthandoff: 04/05/2017

---
# <a name="visual-c-structures-in-class-designer"></a>類別設計工具中的 Visual C++ 結構
類別設計工具支援 C++ 結構，其使用 `struct` 關鍵字所宣告。 以下是一個範例：  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 如需使用 `struct` 類型的詳細資訊，請參閱 [struct](/cpp/cpp/struct-cpp)。  
  
 類別圖表中的 C++ 結構圖形外觀和運作方式類似類別圖形，不同之處在於標籤會讀為 **Struct**，而且有方角而非圓角。  
  
|Code 項目|類別設計工具檢視|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> 結構|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual C++ 程式碼 (類別設計工具)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [類別和結構](/cpp/cpp/classes-and-structs-cpp)   
 [struct](/cpp/cpp/struct-cpp)
