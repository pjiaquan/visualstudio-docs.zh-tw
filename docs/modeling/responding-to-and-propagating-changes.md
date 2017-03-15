---
title: "回應及傳播變更 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 事件"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# 回應及傳播變更
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當項目所建立、 刪除或更新時，您可以撰寫會傳播變更的模型中，其他部分，或外部的資源，例如檔案、 資料庫或其他元件的程式碼。  
  
## 在本節中  
 一般而言，請考慮這些技巧，以下列順序：  
  
|技術|案例|如需詳細資訊|  
|--------|--------|------------|  
|定義計算定義域屬性。|網域屬性，其值計算從模型中的其他屬性。  比方說，是相關的項目價格總額價格。|[計算和自訂的儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|將自訂儲存網域屬性定義。|網域屬性，儲存在模型的還是在外部的其他部分。  比方說，您無法剖析運算式字串組合成模型中的樹狀目錄。|[計算和自訂的儲存體屬性](../modeling/calculated-and-custom-storage-properties.md)|  
|覆寫變更處理常式，例如 OnValueChanging 和 OnDeleting|不同的項目同步，保留以及外部的值與模型的同步處理。<br /><br /> 限制值，以定義的範圍。<br /><br /> 之前及之後呼叫屬性值和其他的變更。  您可以藉由擲回例外狀況結束該變更。|[網域屬性值變更處理常式](../modeling/domain-property-value-change-handlers.md)|  
|規則|您可以定義佇列中等待變更發生的交易結尾之前執行的規則。  它們不會執行復原或取消復原上。  您可以使用它們來持續存放區的某一部分與另一個的同步處理。|[規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)|  
|儲存區事件|模組化存放區提供告知的事件，例如新增或刪除項目或連結，或變更屬性的值。  事件也會執行復原和取消復原。  使用儲存區事件來更新存放區中所沒有的值。|[事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 事件|圖形會有回應按滑鼠和其他筆勢的事件處理常式。  您必須註冊這些事件，為每個物件。  註冊通常是 InitializeInstanceResources，覆寫，都必須分別為每個項目。<br /><br /> 這些事件通常發生於外部交易。|[如何：攔截圖案或 Decorator 上的點選](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)|  
|範圍規則|範圍規則特別用於限制圖形的界限。|[BoundsRules 限制圖案位置和大小](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|選取規則|選取規則特別限制使用者可選取。|[如何：存取及限制目前的選取範圍](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|指出模型項目狀態使用的圖案及連接線，如陰影、 箭頭、 色彩和線條寬度和樣式的功能。|[更新圖案和接點來反映模型](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **比較規則與儲存區事件**  
 在模型中發生變更時，會執行變更 notifiers、 規則和事件。  
  
 在結束交易中發生變更，通常會套用規則，並認可交易中的變更之後，會套用事件。  
  
 使用儲存區事件來同步處理的模型與物件外的存放區和規則，以維持在存放區內的一致性。  
  
-   **建立自訂規則**您做為抽象的統治的衍生類別中建立自訂規則。  此外，您也必須通知相關的自訂規則的架構。  如需詳細資訊，請參閱 [規則傳播模型內的變更](../modeling/rules-propagate-changes-within-the-model.md)。  
  
-   **訂閱事件**您可以訂閱事件之前，先建立事件處理常式和委派。  然後使用<xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>屬性，以訂閱該事件。  如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
-   **復原變更**當您復原交易時，會引發事件，但不是會套用規則。  如果將值變更的規則，而且您復原該變更，此值會重設為原來的值在復原動作。  當引發事件時，您必須以手動方式值變更回其原始值。  若要深入了解 transactons 和復原，請參閱[如何：使用異動更新模型](../modeling/how-to-use-transactions-to-update-the-model.md)。  
  
-   **將事件引數傳遞至規則和事件**這兩個事件和規則會傳送`EventArgs`參數有相關的資訊模型的變更。  
  
## 請參閱  
 [如何：攔截圖案或 Decorator 上的點選](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)   
 [撰寫程式碼來自訂定義域專屬語言](../modeling/writing-code-to-customise-a-domain-specific-language.md)