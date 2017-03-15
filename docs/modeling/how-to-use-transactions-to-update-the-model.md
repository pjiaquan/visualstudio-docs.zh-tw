---
title: "如何：使用異動更新模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# 如何：使用異動更新模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

交易確認存放區中所做的變更會被視為一個群組。  變更群組可被認可或復原交易當成單一單位。  
  
 您的程式碼修改、 加入，或刪除任何項目中的存放區中的每次[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]視覺化和模型的 SDK，則必須在交易內執行操作。  必須有使用中的例項的<xref:Microsoft.VisualStudio.Modeling.Transaction>發生變更時，與儲存區相關聯。  這適用於所有的模型項目、 關聯、 圖形、 圖表和它們的屬性。  
  
 交易的機制，可協助您避免不一致的狀態。  如果交易期間發生錯誤，會復原所有變更。  只有在使用者執行 \[復原\] 指令，每個新的交易將會被視為單一的步驟。  使用者無法復原最近的變更的部分，除非您明確地放入不同的交易。  
  
## 開啟交易  
 管理交易的最方便的方法是使用`using`陳述式放在`try...catch`陳述式：  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 如果例外狀況會使最終`Commit()` ，就會發生進行變更時，儲存區會被重設為先前的狀態。  這可協助您確定錯誤不會在不一致的狀態使模型。  
  
 您可以將任何數目的一筆交易內的變更。  您可以開啟新的交易，在使用中的交易內。  巢狀的交易必須認可或復原包含交易結束之前。  如需詳細資訊，請參閱範例<xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>屬性。  
  
 若要維持變更後的設定，請您應該`Commit`交易之前將它處置。  如果未攔截到在交易內發生例外狀況，所做的變更前的狀態將會重設的存放區。  
  
## 正在復原交易  
 若要確保會保留在存放區，或還原到之前的交易狀態，您可以使用這些策略的其中一個：  
  
1.  引發的交易範圍內未攔截到例外狀況。  
  
2.  明確地還原此交易：  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## 交易不會影響非儲存區物件  
 交易僅管理儲存區的狀態。  它們不能復原部分對外部項目，例如檔案、 資料庫或您的 DSL 定義之外的一般型別宣告的物件所做的變更。  
  
 如果例外狀況可能會讓這類變更存放區的不一致，您應該處理這個例外狀況處理常式中的可能性。  請確定外部資源保持同步使用存放區物件的一種方法是藉由使用事件處理常式，店內項目的結合每個外部物件。  如需詳細資訊，請參閱 [事件處理常式傳播模型外的變更](../modeling/event-handlers-propagate-changes-outside-the-model.md)。  
  
## 在交易結尾處的規則火  
 在交易的最後，處置交易之前，就會引發規則附加到存放區中的項目。  每個規則是一種方法套用至某個已變更的模型項目。  比方說，有更新的圖形狀態，其模型項目已變更時，「 修正 」 規則，並建立模型項目時，會建立圖形。  沒有任何指定的引發順序。  在規則所做的變更將可以觸發其他規則。  
  
 您可以定義自己的規則。  如需規則的詳細資訊，請參閱[回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
 在 \[復原\]、 \[取消復原或 \[復原\] 指令之後不要規則引發。  
  
## 交易內容  
 每個交易，包含的字典，您可以在其中儲存任何您想要的資訊：  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 這特別適用於規則間轉送資訊。  
  
## 異動狀態  
 在某些情況下，您必須避免傳播變更，如果變更導致復原或取消交易復原。  這可能會發生，例如，如果您撰寫可以更新存放區中的另一個值的屬性值處理常式。  復原作業會將存放區中的所有值重都設成其先前的狀態，因為它不需要以計算更新的值。  使用這段程式碼：  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 一開始從檔案載入存放區時，就可以引發規則。  若要避免回應這些變更，請使用：  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```