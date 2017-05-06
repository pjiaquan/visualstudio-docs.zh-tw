---
title: "如何：在 Office 專案中建立事件處理常式"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "事件處理常式 [Visual Studio 中的 Office 程式開發]"
  - "事件 [Visual Studio 中的 Office 程式開發]"
  - "Visual Basic [Visual Studio 中的 Office 程式開發], 事件處理常式"
  - "Visual C# [Visual Studio 中的 Office 程式開發], 事件處理常式"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：在 Office 專案中建立事件處理常式
  在 Visual Basic 和 C\# 中建立事件處理常式的方法有數種。  在設計檢視中，您可以按兩下控制項以建立控制項的預設事件處理常式，或是使用 \[**屬性**\] 視窗的事件窗格，為控制項中的任何事件建立處理常式。  但是，如果您是在 \[程式碼\] 檢視中，您可能不想為了建立事件處理常式而切換至 \[設計\] 檢視。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 若要在 Visual Basic 中建立事件處理常式  
  
1.  從程式碼編輯器頂端的 \[**類別名稱**\] 清單中，選取您要為其建立事件處理常式的物件。  
  
    > [!NOTE]  
    >  如果想要為 `ThisDocument` 或 `ThisWorkbook` 建立事件處理常式，您必須在 \[**類別名稱**\] 下拉式清單中選取 \[**\(ThisDocument 事件\)**\] 或 \[**\(ThisWorkbook 事件\)**\]  
  
2.  從程式碼編輯器頂端的 \[**方法名稱**\] 下拉式清單中，選取事件。  
  
     Visual Studio 會建立事件處理常式，並將插入點移到剛建立的事件處理常式。  如果事件處理常式已經存在，插入點便會移到現有的事件處理常式。  
  
### 若要在 C\# 中建立事件處理常式  
  
1.  在類別的 **Startup** 事件中建立事件委派，方法是輸入限定事件名稱，後面加上一個空格，然後輸入 \+\= \(後面不加任何空格\)。  例如：  
  
     `this.<object name>.<event name> +=`  
  
2.  在程式碼行結尾，按兩次 TAB 鍵。  
  
     Visual Studio 會自動完成程式碼行、建立事件處理常式，然後將插入點移到剛建立的事件處理常式。  
  
## 請參閱  
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)  
  
  