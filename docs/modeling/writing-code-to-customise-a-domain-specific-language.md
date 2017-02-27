---
title: "撰寫程式碼來自訂定義域專屬語言 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "定義域專屬語言程式設計"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# 撰寫程式碼來自訂定義域專屬語言
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本節會示範如何使用自訂的程式碼來存取、 修改或建立以網域特定語言的模型。  
  
 有幾種內容，您可以在此撰寫 DSL 的情況下運作的程式碼：  
  
-   **自訂命令。** 您可以建立一個使用者可以在圖表上按一下滑鼠右鍵來叫用，以及其修改模型的指令。  如需詳細資訊，請參閱 [如何：在捷徑功能表中加入命令](../Topic/How%20to:%20Add%20a%20Command%20to%20the%20Shortcut%20Menu.md)。  
  
-   **驗證。** 您可以撰寫程式碼，確認模型\] 是在正確的狀態。  如需詳細資訊，請參閱 [定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。  
  
-   **覆寫預設行為。** 您可以修改產生的程式碼是從 DslDefinition.dsl 的許多方面。  如需詳細資訊，請參閱 [覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。  
  
-   **文字轉換。** 您可以撰寫包含存取模型，並會產生文字檔案時，要產生程式碼範例的程式碼的文字範本。  如需詳細資訊，請參閱 [從網域指定的語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
-   **其他 Visual Studio 的擴充功能。** 您可以撰寫個別的 VSIX 擴充功能，以讀取和修改模型。  如需詳細資訊，請參閱[如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)。  
  
 您在 DslDefinition.dsl 中定義類別的執行個體保存在一種資料結構，呼叫*於記憶體中存放區* \(IMS\) 或 *存放區*。  您永遠在 DSL 中定義的類別供存放區做為引數的建構函式。  例如，如果您的 DSL 定義類別，稱為範例：  
  
 `Example element = new Example (theStore);`  
  
 將物件保留在存放區 \(而非只是像一般的物件\) 提供數個好處。  
  
-   **交易**。  您可以將一系列的相關變更為交易：  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     如果發生例外狀況時所做的變更，這樣就不會執行最後的 Commit\(\)，儲存區會重設為其先前的狀態。  這可協助您確定錯誤不會在不一致的狀態使模型。  如需詳細資訊，請參閱 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **「 二元 」 關係**。  如果您定義兩個類別之間的關係，在兩端的執行個體就會有一個巡覽到另一端的屬性。  這兩個部分一定會同步處理。  比方說，如果您是使用名為父代和子系的角色定義 parenthood 關聯性，您可以撰寫：  
  
     `John.Children.Add(Mary)`  
  
     現在，如果兩個以下的運算式都成立：  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     您也可以撰寫來達成相同的效果：  
  
     `Mary.Parents.Add(John)`  
  
     如需詳細資訊，請參閱 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)。  
  
-   **規則與事件**。  您可以定義指定的變更時引發的規則。  會使用規則，比方說，讓圖形保持在圖表上保持在最新狀態所呈現的模型項目。  如需詳細資訊，請參閱 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
-   **序列化**。  存放區提供了標準的方式，用來序列化至檔案包含的物件。  您可以自訂序列化和還原序列化的規則。  如需詳細資訊，請參閱 [自訂檔案儲存體和 XML 序列化](../modeling/customizing-file-storage-and-xml-serialization.md)。  
  
## 請參閱  
 [自訂及擴充網域指定的語言](../modeling/customizing-and-extending-a-domain-specific-language.md)