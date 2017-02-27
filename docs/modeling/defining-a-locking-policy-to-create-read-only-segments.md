---
title: "定義鎖定原則來建立唯讀區段 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 12
---
# 定義鎖定原則來建立唯讀區段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

不變性 API 的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]視覺化和模型的 SDK 能讓程式鎖定部份或全部的定義域專屬語言 \(DSL\) 模型，讓它可以讀取但不是會變更。  無法使用這個唯讀選項，比方說，以便使用者可以要求和您的同事加上註解以及檢閱 DSL 模型，但不可以讓他們變更原始檔案。  
  
 此外，DSL 作者，您可以定義*鎖定原則。* 鎖定的原則會定義何種鎖定是允許、 不允許的或強制。  比方說，當您發佈 DSL 時，您可以鼓勵協力廠商開發人員，可以將其延伸，以新命令。  但是，您也可以使用鎖定的原則，以防止其遭到修改模型的指定組件的唯讀狀態。  
  
> [!NOTE]
>  使用反映，可以規避鎖定的原則。  它對於協力廠商開發人員，提供清楚的界限，但並不會提供更強的安全性。  
  
 更多的資訊和範例是在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][視覺化和模型的 SDK](完整.嗎？LinkId%20=%20186128)的網站。  
  
## 設定和取得鎖定  
 存放區、 磁碟分割，或個別的項目，您可以設定鎖定。  比方說，這個陳述式會防止不慎被刪除的模型項目，並將也防止它的屬性變更:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 其他鎖定值可用來防止變更關聯性、 項目建立、 磁碟分割及 re\-ordering 的連結，在角色間移動。  
  
 使用者動作和程式碼，就會套用鎖定。  如果程式碼會嘗試進行的變更， `InvalidOperationException`就會擲回。  復原或取消復原作業，鎖定會略過。  
  
 您可能發現其他項目是否有任何鎖定組中使用`IsLocked(Locks)` ，您可以使用，以取得目前的項目上的鎖定集`GetLocks()`。  
  
 您可以設定鎖定，而不使用交易。  儲存區的一部分的未鎖定資料庫。  如果您設定的鎖定次數值變更回存放區中，例如在 OnValueChanged，您應該讓屬於復原作業的變更。  
  
 這些方法都是擴充方法中所定義的<xref:Microsoft.VisualStudio.Modeling.Immutability>命名空間。  
  
### 鎖定的磁碟分割上，並儲存  
 鎖定也會套用到資料分割和存放區。  一種鎖，如果您將套用於資料分割中的所有項目。  因此，比方說，下列陳述式會防止在磁碟分割的所有項目不慎被刪除，無論他們自己的鎖定狀態。  不過，其他鎖定例如`Locks.Property`仍無法安裝個別的項目：  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 鎖定的儲存區上設定適用於其所有元素，不論該鎖定的磁碟分割和項目上的設定。  
  
### 使用鎖定  
 您可以使用鎖定，以便執行配置，如下列範例：  
  
-   不允許變更所有的項目和關聯性，除了代表註解。  這可讓使用者加上註解而不變更它的模型。  
  
-   不允許變更預設的磁碟分割，但允許變更圖表的資料分割中。  使用者可以重新排列圖表中，但不能變更基礎的模型。  
  
-   不允許一群獨立的資料庫中註冊的使用者以外的存放區的變更。  對於其他的使用者，圖表\] 和 \[模型是唯讀。  
  
-   不允許變更模型，如果圖表的布林值屬性設定為 true。  提供功能表指令來變更該屬性。  這有助於確保它們不會使的使用者不小心變更。  
  
-   不允許新增和刪除的項目關聯的特定類別，但允許屬性變更。  這能讓使用者以固定的表單，可以在其中填入內容。  
  
## 鎖定值  
 在存放區、 磁碟分割或個別的 ModelElement，可以設定鎖定。  鎖定是`Flags`列舉型別： 您可以結合使用其值 ' &#124;'。  
  
-   鎖定的 ModelElement 必定會包含其資料分割的鎖定。  
  
-   鎖定的磁碟分割加上存放區的鎖定。  
  
 您無法在磁碟分割設定鎖定或儲存，並同時停用個別的項目上的鎖定。  
  
|值|這表示如果`IsLocked(Value)`為真|  
|-------|------------------------------|  
|None|沒有限制。|  
|屬性|無法變更網域內容的項目。  這並不適用於網域類別在關聯性的角色所產生的屬性。|  
|Add|在磁碟分割，則無法建立新的項目和連結或儲存。<br /><br /> 不適用於`ModelElement`。|  
|移動|無法磁碟分割之間移動項目，如果`element.IsLocked(Move)`為 true，如果`targetPartition.IsLocked(Move)`為 true。|  
|Delete|如果這個鎖住設定項目本身，或在任何的項目刪除會傳播，例如內嵌的項目和圖形，就無法刪除項目。<br /><br /> 您可以使用`element.CanDelete()`探索是否可以刪除項目。|  
|重新排列|無法變更排序在 roleplayer 的連結。|  
|RolePlayer|無法變更組會在這個項目中取得資料來源的連結。  比方說，新的項目不能嵌入這個項目下方。  這並不會影響其這個項目做為目標的連結。<br /><br /> 如果這個項目是連結，它的來源和目標都不會受到影響。|  
|全部|其他值的位元 OR 運算。|  
  
## 鎖定的原則  
 為 DSL 作者，您可以定義*鎖定原則*。  鎖定的原則 moderates SetLocks\(\)，的作業，以便您可以防止特定的鎖定設定，或強制特定的鎖定必須先設定。  一般而言，您可使用鎖定的原則，若要防止使用者或開發人員不小心 contravening DSL 的用途，以相同的方式，您可以宣告變數`private`。  
  
 您也可以使用鎖定的原則來設定所有的項目上的鎖定項目的型別而定。  這是因為`SetLocks(Locks.None)`通稱為第一次建立項目或從檔案還原序列化時。  
  
 不過，您不能使用原則來變更其生命週期的項目上的鎖定。  若要達成該效果，您應該使用呼叫`SetLocks()`。  
  
 若要定義鎖定的原則，您必須：  
  
-   建立一個類別，實作<xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>。  
  
-   這個類別加入的服務，都是透過您的 DSL 的 DocData。  
  
### 若要定義鎖定的原則  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>具有下列定義：  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 要發出呼叫時，會呼叫這些方法`SetLocks()`在存放區、 磁碟分割或 ModelElement。  在每個方法中，您可以用一組建議的鎖定。  您可以返回已提議的設定，或可加入和減去鎖定。  
  
 例如：  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 若要確定使用者隨時都可以刪除的項目，即使其他程式碼會呼叫`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 不允許在每個項目的 MyClass 的所有屬性的變更：  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### 若要使用您的原則做為服務  
 在您`DslPackage`專案、 加入新的檔案包含類似下列的範例的程式碼：  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```