---
title: "Additional Information About Class Designer Errors | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound"
  - "vs.classdesigner.CPlusPlusNoTypeFound"
  - "vs.classdesigner.CannotShowBaseType"
  - "vs.classdesigner.MatchOrphanTypesAtLoad"
  - "vs.classdesigner.CannotShowType"
  - "vs.classdesigner.AssociationTypeNotFoundError"
  - "vs.classdesigner.ViewInDiagramNoTypesFound"
  - "vs.classdesigner.CannotImplementInterface"
  - "vs.classdesigner.CannotShowImplementedInterface"
  - "vs.classdesigner.ViewInDiagramUnparsableTypeFound"
  - "vs.classdesigner.AssociationTypeNotFound"
  - "vs.classdesigner.CPlusPlusTypeCannotBeAdded"
helpviewer_keywords: 
  - "errors, class diagrams"
  - "errors, Class Designer"
  - "error messages, Class Designer"
  - "Class Designer [Visual Studio], errors"
  - "error messages, class diagrams"
  - "class diagrams, errors"
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Additional Information About Class Designer Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

類別設計工具不會追蹤原始程式檔的位置，因此，修改您的專案結構或移動專案中的原始程式檔，可能會導致類別設計工具遺失類型的追蹤，特別是 typedef、基底類別或關聯類型的來源類型。  您可能會收到 **Class Designer is unable to display this type** 之類的錯誤。  如果您收到錯誤訊息，請將已修改或重新配置的原始程式碼再次拖曳到類別圖表中，以重新顯示。  
  
 您可以在下列資源中找到其他錯誤和警告的協助：  
  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)  
 包含有關在類別圖中顯示 C\+\+ 的疑難排解資訊。  
  
 [Visual Studio 類別設計工具論壇](http://go.microsoft.com/fwlink/?LinkId=160754)  
 提供類別設計工具相關問題的論壇。  
  
## 請參閱  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)