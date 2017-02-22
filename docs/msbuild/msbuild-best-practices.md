---
title: "MSBuild 最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "最佳作法, MSBuild"
  - "MSBuild, 最佳作法"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 最佳做法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：  
  
-   處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。  例如，使用  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   當您選取項目時，請避免使用萬用字元，  而要明確地指定檔案。  這樣會比較容易追蹤當您新增或刪除檔案時，可能發生的錯誤。  
  
## 請參閱  
 [進階概念](../msbuild/msbuild-advanced-concepts.md)