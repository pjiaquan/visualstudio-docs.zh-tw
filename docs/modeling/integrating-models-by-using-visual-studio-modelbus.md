---
title: "使用 Visual Studio Modelbus 整合模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用 Visual Studio Modelbus 整合模型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 提供方法來建立模型的模型之間及其他工具的連結。 例如，您可以連結定義域專屬語言 \(DSL\) 模型和 UML 模型。 您可以建立一組整合的 Dsl。  
  
 ModelBus 可讓您建立模型或模型內的特定項目唯一的參考。 此參考可以儲存在模型中，外部，例如在另一個模型中的項目。 時的情況下，工具需要取得項目的存取權，模型匯流排基礎結構會載入適當的模型，並傳回的項目。 如果您想，您可以向使用者顯示模型。 如果無法在先前的位置存取檔案，ModelBus 會請使用者尋找檔案。 如果使用者找到檔案，ModelBus 會修正該檔案的所有參考。  
  
> [!NOTE]
>  在目前 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus，連結的模型的實作必須是在相同的項目 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案。  
  
 如需詳細資訊和範例程式碼，請參閱︰  
  
-   [如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modeling SDK for Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> 提供存取權給 DSL  
 您可以建立模型或其項目的 ModelBus 參考之前，您必須定義 dsl 的 ModelBusAdapter。 若要這樣做最簡單的方法是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型匯流排擴充功能，將命令加入至 DSL 設計工具。  
  
###  <a name="expose"></a> 若要公開 （expose） 給模型匯流排 DSL 定義  
  
1.  下載並安裝 Visual Studio 模型匯流排擴充功能，除非您已安裝它。 如需詳細資訊，請參閱 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
2.  開啟 DSL 定義檔。 以滑鼠右鍵按一下設計介面，然後按一下 \[ **啟用 Modelbus**。  
  
3.  在對話方塊中，選擇 \[ **我想要這個 DSL 公開給 ModelBus**。 如果您想要這個 DSL 公開給其模型並使用其他 Dsl 的參考，您可以選擇這兩個選項。  
  
4.  按一下 \[確定\]。 新的專案"ModelBusAdapter"會加入至 DSL 方案。  
  
5.  如果您想要從文字範本存取 DSL，您必須修改新的專案中的 AdapterManager.tt。 如果您想要從命令和事件處理常式等其他程式碼存取 DSL，請省略這個步驟。 如需詳細資訊，請參閱[使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)。  
  
    1.  變更到 AdapterManagerBase 的基底類別 <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  
  
    2.  檔案結尾附近插入這個額外的屬性類別 adaptermanager 的前面︰  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  在參考的 ModelBusAdapter 專案中，加入 **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**。  
  
     如果您想要從文字範本和其他程式碼存取 DSL，您需要兩張介面卡，已修改，另一個未經修改。  
  
6.  按一下 \[ **轉換所有範本**。  
  
7.  重建方案。  
  
 它現在可以為 modelbus 開啟這個 DSL 的執行個體。  
  
 資料夾 `ModelBusAdapters\bin\*` 包含所建置的組件 `Dsl` 專案和 `ModelBusAdapters` 專案。 若要從另一個 DSL 參考這個 DSL，您應該匯入這些組件。  
  
### 確定可以參考項目  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 配接器會使用項目的 guid 來識別它，預設情況下。 因此必須模型檔案中保存這些識別項。  
  
##### 若要確保會保存 Id 項目  
  
1.  開啟 DslDefinition.dsl。  
  
2.  在 \[DSL 總管\] 中，展開 **Xml 序列化行為**, ，然後 **類別資料**。  
  
3.  針對每個類別，您要建立模型匯流排參考︰  
  
     按一下 \[類別\] 節點，並在 \[屬性\] 視窗中，請確定 **序列化 Id** 設為 `true`。  
  
 或者，如果您想要使用的項目名稱來識別項目，而不是 guid，您可以覆寫產生之配接器的部分。 覆寫配接器類別中的下列方法︰  
  
-   覆寫 `GetElementId` 可傳回您想要使用的識別碼。 建立參考時，會呼叫這個方法。  
  
-   覆寫 `ResolveElementReference` 找出正確的項目從模型匯流排參考。  
  
##  <a name="editRef"></a> 從另一個 DSL 存取 DSL  
 您可以在 DSL 中，網域屬性中儲存模型匯流排參考，而且您可以撰寫自訂程式碼使用它們。 您也可以讓使用者藉由選取的模型檔案和項目中的建立模型匯流排參考。  
  
 若要啟用的 DSL 使用另一個 DSL 的參考，您應該先將它 *消費者* 的模型匯流排參考。  
  
#### 若要啟用 DSL 使用已公開 DSL 的參考  
  
1.  在 DSL 定義圖表中，以滑鼠右鍵按一下圖表的主要部分，然後按一下 \[ **啟用 Modelbus**。  
  
2.  在對話方塊中，選取 **我想要啟用這個模型使用模型匯流排參考**。  
  
3.  在使用 DSL 的 Dsl 專案中，加入下列組件加入專案參考。 公開的 DSL 的 ModelBusAdapter\\bin\\ \* 目錄中，您會發現這些組件 （.dll 檔案）。  
  
    -   公開的 DSL 組件，例如 **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   公開的模型匯流排配接器組件，例如 **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  使用 DSL 專案的專案參考中加入下列.NET 組件。  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### 網域屬性中儲存模型匯流排參考  
  
1.  在使用 DSL 的 DSL 定義中，將網域屬性加入至網域類別，並設定其名稱。  
  
2.  在 \[屬性\] 視窗中，選取此選項，網域屬性將 **類型** 到 `ModelBusReference`。  
  
 在這個階段，程式碼可設定屬性值，但它是唯讀屬性\] 視窗中。  
  
 您可以讓使用者能夠設定具有特殊的 ModelBus 參考編輯器的屬性。 有兩個版本，這個編輯器或 *選擇器︰* 其中一個可讓使用者選擇模型檔，以及其他可讓使用者選擇模型檔和模型內的項目。  
  
#### 若要允許使用者設定網域屬性中的模型匯流排參考  
  
1.  以滑鼠右鍵按一下網域屬性，然後按一下 **編輯 ModelBusReference 特定屬性**。 對話方塊隨即開啟。 這是 *模型匯流排選擇器*。  
  
2.  選取適當 **modelbusreference 類型**︰ 模型或模型內的項目。  
  
3.  在檔案對話方塊篩選字串中，輸入字串，例如 `Family Tree files |*.ftree`。 替代，以反映您公開的 DSL 的副檔名。  
  
4.  如果您選擇在模型中某個項目的參考，您可以新增類型的清單，使用者可以選擇，例如 Company.FamilyTree.Person。  
  
5.  按一下 \[ **確定**, ，然後按一下 \[ **轉換所有範本** \[方案總管\] 工具列。  
  
    > [!WARNING]
    >  如果您尚未選取有效的模型或實體，\[確定\] 按鈕必須沒有作用，即使它可能會顯示為已啟用。  
  
6.  如果您指定的目標型別 （例如 company.familytree.person） 清單，然後您必須加入您的 DSL 專案的組件參考參考目標 DSL，例如 Company.FamilyTree.Dsl.dll DLL  
  
#### 若要測試模型匯流排參考  
  
1.  建立公開和取用的 Dsl。  
  
2.  執行其中一個 Dsl 在實驗模式中按下 F5 或 CTRL \+ F5。  
  
3.  在實驗性執行個體中的偵錯專案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，新增的每個 DSL 執行個體的檔案。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 只可以解析參考模型項目在同一個 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案。 比方說，您無法在另一個組件的檔案系統中建立模型檔案的參考。  
  
4.  建立公開的 DSL 執行個體中的某些項目和連結，並加以儲存。  
  
5.  開啟使用 DSL 的執行個體，並選取模型匯流排參考屬性的模型項目。  
  
6.  在 \[屬性\] 視窗中，按兩下模型匯流排參考屬性。 選擇器\] 對話方塊隨即開啟。  
  
7.  按一下 \[ **瀏覽** ，然後選取 \[公開的 DSL 執行個體。  
  
     選擇器也可讓您選擇的項目在模型中，如果您指定的模型匯流排參考特定的項目類型。  
  
## 建立程式碼中的參考  
 當您想要儲存模型或模型內的項目參考時，您會建立 `ModelBusReference`。 有兩種類型的 `ModelBusReference`︰ 模型參考和項目參考。  
  
 若要建立模型參考，您需要模型是一個執行個體和檔名的 DSL 的 AdapterManager 或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 模型的專案項目。  
  
 若要建立項目參考，您需要配接器模型檔案及您想要參考的項目。  
  
> [!NOTE]
>  使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus，您可以在同一個建立項目的參考 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案。  
  
### 匯入公開的 DSL 組件  
 在使用專案中，加入公開的 DSL 的 DSL 和 ModelBusAdapter 組件的專案參考。  
  
 例如，假設您想要在 MusicLibrary DSL 的項目中儲存 ModelBus 參考。 ModelBus 參考會參考 FamilyTree DSL 的項目。 在 `Dsl` MusicLibrary 方案，在 \[參考\] 節點中的專案加入下列組件的參考︰  
  
-   Fabrikam.familytree.dsl.dll\-已公開的 DSL。  
  
-   Fabrikam.familytree.modelbusadapters.dll\-已公開 DSL 的 ModelBus 配接器。  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 這些組件位於 `ModelBusAdapters` 公開的 DSL 專案下 `bin\*`。  
  
 在您將在其中建立參考程式碼檔案，您通常必須匯入這些命名空間︰  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### 若要建立模型的參考  
 若要建立模型參考，您可以存取公開 DSL 的 AdapterManager，並用來建立模型的參考。 您可以指定檔案路徑，或 `EnvDTE.ProjectItem`。  
  
 您可以從 AdapterManager 取得配接器，可讓您存取模型中的個別項目。  
  
> [!NOTE]
>  當您完成使用它，您必須處置配接器。 為了達到這個目的最方便的方法是使用 `using` 陳述式。 下列範例將說明這點。  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 如果您想要能夠使用 `modelReference` 之後，您可以將它儲存在具有外部類型的網域屬性 `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 若要允許使用者編輯這個網域屬性，請使用 `ModelReferenceEditor` 做為編輯器屬性的參數。 如需詳細資訊，請參閱 [允許使用者編輯參考](#editRef)。  
  
### 若要建立之項目的參考  
 模型建立配接器可以用於建立及解析參考。  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 如果您想要能夠使用 `elementReference` 之後，您可以將它儲存在具有外部類型的網域屬性 `ModelBusReference`。 若要允許使用者對其進行編輯，請使用 `ModelElementReferenceEditor` 做為編輯器屬性的參數。 如需詳細資訊，請參閱 [允許使用者編輯參考](#editRef)。  
  
### 解析參考  
 如果您有 `ModelBusReference` \(MBR\) 您可以在模型或取得所參考的模型項目。 如果項目會顯示圖表或其他檢視，您可以開啟檢視，並選取項目。  
  
 您可以從 MBR 建立配接器。 從配接器，您可以取得模型的根。 您也可以解析參考模型內之特定元素的 Mbr。  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### 若要解決文字範本中的 ModelBus 參考  
  
1.  您想要存取的 DSL 必須具有存取設定文字範本的 ModelBus 配接器。 如需詳細資訊，請參閱[提供存取權給 DSL](#provide)。  
  
2.  一般而言，您將存取儲存在來源 DSL 的 DSL 使用模型匯流排參考 \(MBR\) 的目標。 因此，您的範本包含來源 DSL，再加上程式碼的指示詞，用於解析 MBR。 如需文字範本的詳細資訊，請參閱 [從網域指定的語言產生程式碼](../modeling/generating-code-from-a-domain-specific-language.md)。  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 如需詳細資訊和逐步解說，請參閱 [使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## 序列化 ModelBusReference  
 如果您想要儲存 `ModelBusReference` \(MBR\) 字串的格式，您可以將它序列化︰  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 以這種方式序列化的 MBR 與內容無關。 如果您使用簡單的檔案架構模型匯流排配接器，MBR 會包含絕對檔案路徑。 這已足以如果執行個體模型檔就永遠不會移動。 不過，模型檔通常會是中的項目 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案。 您的使用者會預期要能夠將整個專案移至檔案系統的不同部分。 它們也會希望能夠保留原始檔控制下的專案，並在不同的電腦上開啟。 因此應相對於專案的檔案所在的位置序列化路徑名稱。  
  
### 序列化相對於指定的檔案路徑  
 A `ModelBusReference` 包含 `ReferenceContext`, ，這是用來儲存資訊，例如檔案路徑，相對於其應該要加以序列化的字典。  
  
 序列化相對於路徑︰  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 若要從字串擷取參考︰  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### 建立其他配接器的 ModelBusReferences  
 下列資訊是很有用，如果您想要建立自己的配接器。  
  
 A `ModelBusReference` \(MBR\) 包含兩個部分︰ 由模型匯流排還原序列化的 MBR 標頭和配接器特定處理的特定配接器的管理員。 這可讓您提供您自己的配接器序列化格式。 例如，您可以參考資料庫，而不是檔案，或您可以在配接器參考儲存其他資訊。 您自己的配接器可以放置中的其他資訊 `ReferenceContext`。  
  
 當您還原序列化 MBR 時，您必須提供 ReferenceContext，然後儲存在 MBR 物件。 當您序列化 MBR 時，儲存的 ReferenceContext 是配接器用來協助產生字串。 已還原序列化的字串不包含 ReferenceContext 中的所有資訊。 例如，在簡單檔案架構的配接器，ReferenceContext 包含根檔案路徑，不會儲存在已序列化的 MBR 字串中。  
  
 MBR 的還原序列化的兩個階段︰  
  
-   `ModelBusReferencePropertySerializer` 是處理 MBR 標頭的標準序列化。 它會使用標準 DSL `SerializationContext` 屬性包，會儲存在 `ReferenceContext` 使用金鑰 `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`。 特別是， `SerializationContext` 應該包含的執行個體 `ModelBus`。  
  
-   您的 ModelBus 配接器處理配接器特定的 MBR 部分。 它可以使用儲存在 ReferenceContext MBR 中的其他資訊。 簡單檔案架構的配接器保存根檔案路徑的索引鍵 `FilePathLoadContextKey` 和 `FilePathSaveContextKey`。  
  
     只有在使用它時，會還原序列化模型檔案中的配接器參考。  
  
## 若要建立模型  
  
### 建立、 開啟及編輯模型  
 下列片段是取自 VMSDK 網站上的狀態機器範例。 它說明如何使用 ModelBusReferences 建立及開啟模型，並取得與模型相關聯的圖表。  
  
 在此範例中，目標 DSL 的名稱為 StateMachine。 多個名稱衍生自，例如模型類別的名稱和 ModelBusAdapter 的名稱。  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## 驗證參考  
 Brokenreferencedetector 會測試所有的網域屬性可儲存 ModelBusReferences 的存放區中。 它會呼叫此動作，您可找到任何動作。 這是驗證方法特別有用。 下列驗證方法測試存放區在嘗試儲存模型，並回報在錯誤視窗中斷的參照︰  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## ModelBus 擴充功能所執行的動作  
 下列資訊不是很重要的但可能會很有用，如果您要擴充使用 ModelBus。  
  
 ModelBus 擴充功能在 DSL 方案中，進行下列變更。  
  
 當您以滑鼠右鍵按一下 DSL 定義圖時，按一下 \[ **啟用 Modelbus**, ，然後選取 **啟用這個 DSL 以使用 ModelBus**:  
  
-   在 DSL 專案中，參考加入至 **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   在 DSL 定義中，加入外部類型參考︰ `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`。  
  
     您可以看到在參考 **DSL Explorer**, 下 **網域類型**。 若要手動加入外部類型參考，以滑鼠右鍵按一下根節點。  
  
-   加入新的範本檔案， **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**。  
  
 當您將網域屬性的型別設定為 ModelBusReference，然後以滑鼠右鍵按一下屬性再按一下 **啟用 ModelBusReference 的特定屬性**:  
  
-   數個 CLR 屬性會加入至定義域屬性。 您可以在 \[屬性\] 視窗中的自訂屬性欄位中看到它們。 在 **Dsl\\GeneratedCode\\DomainClasses.cs**, ，您可以看到屬性宣告的屬性︰  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 當您以滑鼠右鍵按一下 DSL 定義圖時，按一下 \[ **啟用 ModelBus**, ，然後選取 **這個 DSL 公開給 ModelBus**:  
  
-   新的專案 `ModelBusAdapter` 加入至方案。  
  
-   參考 `ModelBusAdapter` 加入至 `DslPackage` 專案。`ModelBusAdapter` 具有參考 `Dsl` 專案。  
  
-   在 **DslPackage\\source.extention.tt**, ，`|ModelBusAdapter|` 加入做為 MEF 元件。  
  
## 請參閱  
 [如何：在程式碼中開啟檔案的模型](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [整合 UML 模型與其他模型及工具](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [如何：加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [使用文字範本中的 Visual Studio ModelBus](../modeling/using-visual-studio-modelbus-in-a-text-template.md)