---
title: "使用文字範本中的 Visual Studio ModelBus | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 使用文字範本中的 Visual Studio ModelBus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您撰寫讀取一個模型，內含的文字範本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 參考的話，您可能想要參考解析為存取目標模型。  在此情況下，您需要額外文字範本和參考的定義域專屬語言 \(Dsl\)：  
  
-   做為目標的參考 DSL 必須要有一個 ModelBus 介面卡已設定為從文字範本的存取。  您也可以存取的 DSL 與其他程式碼，請重新設定介面卡需要除了標準的 ModelBus 介面卡。  
  
     配接器管理員必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> ，而且必須具有屬性`[HostSpecific(HostName)]`。  
  
-   範本必須繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
> [!NOTE]
>  如果您想要閱讀 DSL 模型不包含 ModelBus 的參考，您可以使用指示詞會在您的 DSL 專案中產生的處理器。  如需詳細資訊，請參閱 [從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)。  
  
 如需文字範本的詳細資訊，請參閱[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)。  
  
## 建立模型匯流排介面卡來存取從文字範本  
 如果要解決文字範本中的 ModelBus 參考，目標 DSL 都必須具有相容的介面卡。  文字範本執行從各別 AppDomain 內[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文件的編輯器，並因此配接器已載入的模型，而不是透過 DTE 存取它。  
  
#### 若要建立 ModelBus 配接器相容於文字範本  
  
1.  如果目標 DSL 方案並沒有**ModelBusAdapter**專案，使用 Modelbus 擴充程式精靈建立：  
  
    1.  下載並安裝[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 的副檔名，如果您還沒有如此。  如需詳細資訊，請參閱[視覺化和模型的 SDK](完整.嗎？LinkID%20=%20185579)。  
  
    2.  開啟 DSL 的定義檔。  在設計介面上按一下滑鼠右鍵，然後按一下 \[ **啟用 Modelbus**。  
  
    3.  在對話方塊中，選取 \[ **我想要公開 \(expose\) 這個 DSL 而將 ModelBus**。  如果您想要公開 \(expose\) 其模型和使用其他 Dsl 參考這個 DSL，您可以選取這兩個選項。  
  
    4.  按一下 \[**確定**\]。  "ModelBusAdapter"的新專案加入至 DSL 方案。  
  
    5.  按一下 \[ **轉換所有範本**。  
  
    6.  重建方案。  
  
2.  如果您想要從某文字範本並與其他程式碼，例如指令存取 DSL 複製**ModelBusAdapter**專案：  
  
    1.  在 \[Windows 檔案總管\] 中，複製並貼上所在的資料夾**ModelBusAdapter.csproj**。  
  
    2.  重新命名專案檔 \(例如， **T4ModelBusAdapter.csproj**\)。  
  
    3.  在**方案總管\] 中**，請以滑鼠右鍵按一下方案節點，指向 **新增**，然後按一下 **現有專案**。  找出新的配接器專案中， **T4ModelBusAdapter.csproj**。  
  
    4.  在每個`*.tt`檔案的新專案中，變更命名空間。  
  
    5.  在方案總管中新的專案上按一下滑鼠右鍵，再按 \[內容。  在內容編輯器\] 中，變更產生的組件和預設的命名空間的名稱。  
  
    6.  這樣就有兩個配接器的參考，請在 \[DslPackage\] 專案中，加入新的配接器專案的參考。  
  
    7.  DslPackage\\source.extension.tt，以加入一行參考新的配接器專案。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **轉換所有範本** ，並重建方案。  沒有建置錯誤應該就會發生。  
  
3.  在新的配接器專案中，加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  在 AdapterManager.tt：  
  
    -   變更 AdapterManagerBase 的宣告，使其繼承自<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   檔案結尾附近取代之前的 AdapterManager 類別的 HostSpecific 屬性。  移除下面這一行：  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         請插入下面這一行：  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         這個屬性篩選時，使用 modelbus 消費者會搜尋介面卡的配接器集。  
  
5.  **轉換所有範本** ，並重建方案。  沒有建置錯誤應該就會發生。  
  
## 撰寫可解析 ModelBus 參考某文字範本  
 一般而言，您開始使用範本來讀取並產生 「 來源 」 DSL 的檔案。  此範本會使用來源的 DSL 專案，以讀取來源模型檔中所述的方式，則會產生這個指示詞[從文字範本存取模型](../modeling/accessing-models-from-text-templates.md)。  但是，DSL 的來源包含 「 目標 」 DSL 的 ModelBus 參考。  因此要啟用樣板程式碼，來解析參考，並存取目標 DSL。  您因此必須採用範本，依照下列步驟執行：  
  
-   變更基底類別的範本，以<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>。  
  
-   包括`hostspecific="true"`範本指示詞中。  
  
-   目標 DSL 和它的介面卡，以及啟用 ModelBus，請加入組件的參考。  
  
-   您不需要指示詞所產生目標 DSL 的一部分。  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 執行這個文字範本時， `SourceDsl`指示詞的檔案會載入`Sample.source`。  範本可以存取這個模型中，從開始的項目`this.ModelRoot`。  網域類別以及該 DSL 的屬性，可以使用程式碼。  
  
 此外，範本可以解決 ModelBus 的參考。  參考會指向目標模型，其中的組件指示詞可以讓使用網域類別和屬性，這樣的模型 DSL 的程式碼。  
  
-   如果您不使用指示詞所產生的 DSL 專案，您也應該包含下列。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   使用`this.ModelBus` ModelBus 的存取。  
  
## 逐步解說： 測試會使用 ModelBus 某文字範本  
 在這個逐步解說中，您可以遵循下列步驟：  
  
1.  建立兩個 Dsl。  一個 DSL、 *消費者*，有`ModelBusReference`屬性可參考其他 DSL、 *提供者*。  
  
2.  建立兩個 ModelBus 介面卡提供者中： 一個用於文字範本中，另一個則用於一般的程式碼的存取。  
  
3.  Dsl 的執行個體模型專案中建立單一實驗。  
  
4.  在網域中設定屬性來指向其他模型的一種模型。  
  
5.  撰寫按兩下滑鼠的處理常式開啟會指到的模型。  
  
6.  寫入文字範本，可以載入第一個模型、 遵循參照類型的其他模型，並讀取其他模型。  
  
#### 建構 DSL 可進行存取 ModelBus  
  
1.  建立新的 DSL 方案。  這個範例中，選取 \[工作流程\] 方案範本。  若要設定的語言名稱 `MBProvider` ，並以".provide"的副檔名。  
  
2.  在 DSL 定義圖表中，以滑鼠右鍵按一下靠近頂端，並不是圖表的空白部分，然後按一下**啟用 Modelbus**。  
  
    -   如果看不到**啟用 Modelbus**，您必須下載並安裝 VMSDK ModelBus 副檔名。  在 VMSDK 站台上找到它: [視覺化和模型的 SDK](完整.嗎？LinkID%20=%20185579)。  
  
3.  在**啟用 Modelbus** 對話方塊中，選取**公開 \(expose\) 這個 DSL 而將 ModelBus**，然後按一下 \[ **確定**。  
  
     新的專案中， `ModelBusAdapter`，加入至方案。  
  
 現在，您可以透過 ModelBus 的文字範本可以存取的 DSL。  在程式碼中的命令、 事件處理常式或所有這些作業的 AppDomain 模型檔案編輯器中的規則，就可以解決它的參考。  不過，文字範本各別 AppDomain 內執行，而且被編輯時，無法存取模型。  如果您想要存取這個 DSL 文字範本中的 ModelBus 參考，您必須擁有不同的 ModelBusAdapter。  
  
#### 若要建立 ModelBus 介面卡已設定為文字範本  
  
1.  在 Windows 檔案總管，複製並貼上包含 ModelBusAdapter.csproj 的資料夾。  
  
     命名為 \[T4ModelBusAdapter\] 資料夾。  
  
     重新命名專案檔 T4ModelBusAdapter.csproj。  
  
2.  在方案總管\] 中，加入 T4ModelBusAdapter 至 MBProvider 的方案。  \[方案\] 節點上按一下滑鼠右鍵，指到**新增**，然後按一下 **現有專案**。  
  
3.  \[T4ModelBusAdapter\] 專案節點上按一下滑鼠右鍵，再按 \[內容。  在 \[專案屬性\] 視窗中，變更**組件名稱**和**預設 Namespace** 到`Company.MBProvider.T4ModelBusAdapters`。  
  
4.  在 T4ModelBusAdapter 中每個 \*.tt 檔案，在插入 「 T4"在最後的組件中的命名空間，讓行如下所示。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  在`DslPackage`專案、 加入的專案參考`T4ModelBusAdapter`。  
  
6.  在 DslPackage\\source.extension.tt 中，新增下的面這一行下`<Content>`。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  在`T4ModelBusAdapter`專案、 加入的參考：**Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  開啟 T4ModelBusAdapter\\AdapterManager.tt：  
  
    1.  變更基底類別的 AdapterManagerBase 到<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>。  此組件的檔案現在會類似下列項目。  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  檔案的尾聲，插入下列額外的屬性類別 AdapterManager 的前面。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         結果如下所示。  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. 按一下 **轉換所有的範本**在標題列的方案總管\] 中。  
  
10. 重建方案。  按 f5 鍵。  
  
11. 請確認 DSL 正在按下 f5 鍵。  在實驗性的專案中，開啟`Sample.provider`。  關閉 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的實驗執行個體。  
  
 在文字範本，也在一般的程式碼，現在可以解決這個 DSL 的 ModelBus 參照。  
  
#### 建構 DSL 與 ModelBus 參考網域屬性  
  
1.  使用最少的語言\] 方案範本，以建立新的 DSL。  命名為 MBConsumer 的語言，設定檔案的副檔名為".consume"。  
  
2.  在 DSL 專案，加入 MBProvider DSL 組件的參考。  以滑鼠右鍵按一下`MBConsumer\Dsl\References` ，然後按一下 \[ **加入參考**。  在**瀏覽**索引標籤上，找出`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     這可讓您建立使用 「 其他 」 DSL 的程式碼。  如果您想要建立數個 Dsl 的參考，也將它們加入。  
  
3.  在 DSL 定義圖表中，以滑鼠右鍵按一下圖表，然後按一下**啟用 ModelBus**。  在對話方塊中，選取 \[ **啟用這個 DSL 而將使用 ModelBus**。  
  
4.  在類別中`ExampleElement`，將屬性新增到新網域 `MBR`，並在 \[屬性\] 視窗中，將它的型別設定為`ModelBusReference`。  
  
5.  以滑鼠右鍵按一下圖表上的 \[網域\] 屬性，然後按一下 **特定屬性的編輯 ModelBusReference**。  在對話方塊中，選取 \[ **的模型項目**。  
  
     下列設定檔\] 對話方塊的篩選器。  
  
     `Provider File|*.provide`  
  
     之後的子字串"&#124;"是檔案的 \[選項\] 對話方塊的篩選器。  您可以設定以允許任何檔案使用 \*。 \*  
  
     在**模型項目型別**清單中，輸入提供者 DSL \(比方說，Company.MBProvider.Task\) 中的一或多個網域類別的名稱。  它們可以是抽象類別。  如果清單中留白，則使用者可以設定任何項目的參考。  
  
6.  請關閉此對話方塊，並**轉換所有的範本**。  
  
 您已經建立 DSL 可包含在另一個 DSL 之項目的參考。  
  
#### 在方案中建立另一個檔案的 ModelBus 參考  
  
1.  在 \[MBConsumer\] 方案中，按 CTRL \+ F5。  實驗性的執行個體的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會在中開啟**MBConsumer\\Debugging**專案。  
  
2.  新增複本到 Sample.provide 的**MBConsumer\\Debugging**專案。  這是必要的因為 ModelBus 的參考必須參考同一個方案中的檔案。  
  
    1.  偵錯的專案上按一下滑鼠右鍵，指到**新增**，然後按一下 \[ **現有項目**。  
  
    2.  在**加入項目** \] 對話方塊中，將篩選條件設定為 **的所有檔案 \(\*。 \*\)**。  
  
    3.  巡覽至`MBProvider\Debugging\Sample.provide` ，然後按一下 \[ **新增**。  
  
3.  開啟 `Sample.consume`。  
  
4.  按一下一個範例中的圖形，然後在 \[屬性\] 視窗中，按一下 **\[...\]**的 MBR 」 屬性中。  在對話方塊中，按一下 \[ **瀏覽** ，然後選取`Sample.provide`。  在 \[項目\] 視窗中，展開型別工作並選取其中一個項目。  
  
5.  儲存檔案。  
  
     \(還未關閉的實驗性的執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。\)  
  
 您已建立的模型，包含 ModelBus 參考另一個模型中的項目。  
  
#### 文字範本中的 ModelBus 參考解析  
  
1.  實驗性的執行個體中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，開啟的範例文字範本檔案。  以下列方式設定其內容。  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     請注意下列重點：  
  
    1.  `hostSpecific`和`inherits`屬性的`template`指示詞必須先設定。  
  
    2.  取用者模型存取中的 DSL 所產生的指示詞處理器透過平常的方式。  
  
    3.  組件 」 和 「 匯入的指示詞必須能夠存取 ModelBus 和 DSL 的提供者的型別。  
  
    4.  如果您知道許多 Mbr 連結至相同的模型，最好一次呼叫 CreateAdapter。  
  
2.  儲存範本。  請確認產生的文字檔案如下所示。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### 筆勢的處理常式中將 ModelBus 參考解析  
  
1.  關閉實驗性的執行個體的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，如果它正在執行。  
  
2.  新增名為 MBConsumer\\Dsl\\Custom.cs，並設定其內容如下的檔案。  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  按下 CTRL\+F5 鍵。  
  
4.  實驗性的執行個體中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、 開啟`Debugging\Sample.consume`。  
  
5.  連按兩下一個圖形。  
  
     如果您已設定的 MBR，該項目上，參考的模型會開啟，並在選取的參考項目。  
  
## 請參閱  
 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)