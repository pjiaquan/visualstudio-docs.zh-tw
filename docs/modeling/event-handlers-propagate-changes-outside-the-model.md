---
title: "事件處理常式傳播模型外的變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: af5fbd8973082e92f9609e335314a30eb22595fa
ms.lasthandoff: 02/22/2017

---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>事件處理常式傳播模型外的變更
Visualization and Modeling SDK，在中，您可以定義將變更傳播到外部存放區，例如非存放區變數、 檔案、 模型中其他存放區，或其他資源的存放區事件處理常式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組。 存放區事件處理常式會觸發的事件發生在交易結束之後執行。 它們也會在復原或取消復原作業中執行。 因此，不同於存放區規則存放區事件最適合的更新存放區以外的值。 不同於.NET 事件存放區事件處理常式會註冊接聽類別︰ 您不需要註冊個別的處理常式，每個執行個體。 如需如何選擇不同的方式來處理變更的詳細資訊，請參閱[回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)。  
  
 圖形化介面和其他使用者介面控制項是由存放區事件中的外部資源的範例。  
  
### <a name="to-define-a-store-event"></a>若要定義存放區事件  
  
1.  選擇您想要監視的事件類型。 如需完整清單，查看  <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>.</xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>屬性 每個屬性會對應至事件的類型。 最常使用的事件類型包括︰  
  
    -   `ElementAdded`-觸發模型項目時，關聯性連結、 圖形或連接器建立。  
  
    -   ElementPropertyChanged – 時觸發的值`Normal`網域屬性變更時。 只有當新的和舊值不相等，則會觸發事件。 事件無法用於計算和自訂的儲存體屬性。  
  
         它不能套用至角色屬性對應至關聯性連結。 請改用`ElementAdded`來監視網域關聯性。  
  
    -   `ElementDeleted`– 模型項目之後，將觸發，關聯性、 圖形或連接器已被刪除。 您仍然可以存取屬性值的項目，但有其他項目沒有關聯性。  
  
2.  加入部分類別定義*您的 Dsl***DocData**的個別程式碼檔案中**DslPackage**專案。  
  
3.  事件的程式碼撰寫的方法，如下列範例所示。 它可以是`static`，除非您想要存取`DocData`。  
  
4.  覆寫`OnDocumentLoaded()`登錄處理常式。 如果您有多個處理常式，您可以註冊它們全都放在同一個位置。  
  
 註冊程式碼的位置不重要。 `DocView.LoadView()`是替代的位置。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>使用事件來存放區中的復原調整  
 存放區事件並非通常用來傳播變更在存放區，因為事件處理常式執行認可交易之後。 相反地，您會使用規則存放區。 如需詳細資訊，請參閱[規則傳播變更內模型](../modeling/rules-propagate-changes-within-the-model.md)。  
  
 不過，您可以使用事件處理常式可讓存放區，其他的更新，如果您想讓使用者能復原的原始事件以外的其他更新。 例如，假設小寫字元都是專輯標題中的一般慣例。 您可以撰寫更正為小寫的標題之後使用者已輸入大寫, 的存放區事件處理常式。 但是，使用者可以使用 [復原] 命令來取消您的更正，還原大寫字元。 第二個復原會移除使用者的變更。  
  
 相較之下，撰寫規則存放區執行相同的動作，使用者的變更與您的更正會在相同的交易，讓使用者無法復原的調整，而不會失去原始的變更。  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 如果您寫入更新存放區的事件︰  
  
-   使用`store.InUndoRedoOrRollback`若要避免變更模型項目中復原。 交易管理員會設定所有項目重設回原始狀態存放區中。  
  
-   使用`store.InSerializationTransaction`避免時從檔案載入模型進行變更。  
  
-   您的變更會導致進一步觸發的事件。 請確定您避免無限迴圈。  
  
## <a name="store-event-types"></a>儲存事件類型  
 每個事件類型會對應至 Store.EventManagerDirectory 中的集合。 您可以新增或移除事件處理常式在任何時間，但通常會將文件載入時將其加入。  
  
|`EventManagerDirectory`屬性名稱|執行時|  
|-------------------------------------------|-------------------|  
|ElementAdded|建立網域類別、 網域關聯性、 圖形、 連接線或圖表的執行個體。|  
|ElementDeleted|模型項目已從存放區的項目目錄中移除，不再是來源或目標的任何關聯性。 項目實際上不會從記憶體刪除，但會保留在未來的復原。|  
|ElementEventsBegun|叫用為外部交易的結尾。|  
|ElementEventsEnded|已處理所有其他事件時叫用。|  
|ElementMoved|模型項目已從一個存放區的磁碟分割移到另一個。<br /><br /> 這不被與圖案在圖表上的位置。|  
|ElementPropertyChanged|網域屬性的值已變更。 這不會執行舊與新的值不相等。|  
|RolePlayerChanged|其中一個關聯性的兩個角色 （結尾） 會參考新的項目。|  
|RolePlayerOrderChanged|多重性大於 1 的角色，連結的順序已經變更。|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>另請參閱  
 [回應及傳播變更](../modeling/responding-to-and-propagating-changes.md)   
 [程式碼範例︰ 電路圖表](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

