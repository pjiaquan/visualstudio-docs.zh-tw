---
title: "使用 MEF 擴充您的 DSL |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9a730560e0f19c8e6e58ccc830a95541ae3c5d29
ms.lasthandoff: 02/22/2017

---
# <a name="extend-your-dsl-by-using-mef"></a>使用 MEF 擴充您的 DSL
您可以使用 Managed Extensibility Framework (MEF) 來擴充您的網域特定語言 (DSL)。 您或其他開發人員都能夠撰寫 dsl 的擴充功能，而不需要變更 DSL 定義和程式碼。 這類延伸包括功能表命令、 拖放處理常式，以及驗證。 使用者可以安裝 DSL，然後再選擇性地為其安裝擴充功能。  
  
 此外，當您啟用 MEF DSL 中，很方便您撰寫的一些功能，您的 DSL，即使所有建置與 DSL。  
  
 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>若要啟用要由 MEF 擴充 DSL  
  
1.  建立新資料夾命名為**MefExtension**內**DslPackage**專案。 加入下列檔案︰  
  
     檔案名稱︰`CommandExtensionVSCT.tt`  
  
    > [!IMPORTANT]
    >  此 GUID CommandSetId DslPackage\GeneratedCode\Constants.tt 中定義的相同檔案中設定的 GUID  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#  
    // CmdSet Guid must be defined before master template is included  
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt  
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");  
    string menuidCommandsExtensionBaseId="0x4000";  
    #>  
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>  
    ```  
  
     檔案名稱︰`CommandExtensionRegistrar.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
    ```  
  
     檔案名稱︰`ValidationExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
    ```  
  
     檔案名稱︰`ValidationExtensionRegistrar.tt`  
  
     如果您加入這個檔案，您必須啟用您的 DSL 的驗證使用的參數，在其中**EditorValidation** DSL 總管 中。  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
    ```  
  
     檔案名稱︰`PackageExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
    ```  
  
2.  建立新資料夾命名為**MefExtension**內**Dsl**專案。 加入下列檔案︰  
  
     檔案名稱︰`DesignerExtensionMetaDataAttribute.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
    ```  
  
     檔案名稱︰`GestureExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
    ```  
  
     檔案名稱︰`GestureExtensionController.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionController.tt" #>  
    ```  
  
3.  將下行新增至現有的檔案，稱為**DslPackage\Commands.vsct**:  
  
    ```  
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
    ```  
  
     在現有插入一行`<Include>`指示詞。  
  
4.  `Open DslDefinition.dsl.`  
  
5.  在 DSL 總管 中，選取 **編輯器 \ 驗證**。  
  
6.  在 [屬性] 視窗中，確定其中至少一個屬性名為**使用...** is `true`.  
  
7.  在 方案總管 工具列中按一下 **轉換所有範本**。  
  
     附屬檔案會出現下面每個您所加入的檔案。  
  
8.  建置並執行方案來驗證仍然有效。  
  
 您的 DSL 現在是 MEF 啟用。 您可以撰寫功能表命令、 軌跡處理常式，以及驗證條件約束以 MEF 擴充功能。 您可以在 DSL 方案，以及其他自訂程式碼中撰寫這些擴充功能。 此外，您或其他開發人員可以撰寫個別[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充您的 DSL 的副檔名。  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>MEF 啟用的 dsl 建立擴充功能  
 如果您有存取權給自己或其他人所建立的 MEF 啟用 DSL，您可以為它撰寫延伸模組。 擴充功能可用來將功能表命令、 軌跡處理常式或驗證條件約束。 若要撰寫這些擴充功能，您使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能 (VSIX) 解決方案。 方案中有兩個部分︰ 建置程式碼組件的類別庫專案和封裝組件的 VSIX 專案。  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>若要建立副檔名為 DSL 的 VSIX  
  
1.  建立新的類別庫專案。 若要這樣做，請在**新的專案**對話方塊中，選取**Visual Basic**或**Visual C#** ，然後選取**類別庫**。  
  
2.  在新的類別庫專案，加入 DSL 的組件的參考。  
  
    -   這個組件通常具有名稱結尾為"。Dsl.dll 」。  
  
    -   如果您有存取 DSL 專案，您可以找到組件檔的目錄下**Dsl\bin\\\***  
  
    -   如果您具有存取權的 DSL 的 VSIX 檔案時，您可以將 VSIX 檔案的副檔名變更為 「.zip 」 來尋找組件。 解壓縮.zip 檔案。  
  
3.  加入下列.NET 組件參考︰  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
    -   System.ComponentModel.Composition.dll  
  
    -   System.Windows.Forms.dll  
  
4.  相同方案中建立 VSIX 專案。 若要這樣做，請在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#**，按一下 **擴充性**，然後選取**VSIX 專案**。  
  
5.  在 方案總管 VSIX 專案上按一下滑鼠右鍵，然後按一下 **設定為啟始專案**。  
  
6.  在新的專案中，開啟**source.extension.vsixmanifest**。  
  
7.  按一下 **將內容加入**。 在對話方塊中，設定**內容類型**至**MEF 元件**，和**原始碼專案**您類別庫專案。  
  
8.  加入至 DSL 的 VSIX 參考。  
  
    1.  在**source.extension.vsixmanifest**，按一下 **加入參考**  
  
    2.  在對話方塊中，按一下 **加入裝載**，然後尋找 DSL 的 VSIX 檔案。 在建置 DSL 方案中，在 VSIX 檔案**DslPackage\bin\\\***。  
  
         這可讓使用者一次安裝 DSL 和擴充功能。 如果使用者已安裝 DSL，將會安裝您的擴充。  
  
9. 檢閱及更新的其他欄位**source.extension.vsixmanifest**。 按一下 **選取版本**，並確認正確[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本設定。  
  
10. 類別庫專案中加入程式碼。 使用下一節中的範例，做為指南。  
  
     您可以加入任意數目的命令、 手勢和驗證類別。  
  
11. 若要測試擴充功能，請按**F5**。 在實驗性執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，建立或開啟 DSL 的範例檔案。  
  
## <a name="writing-mef-extensions-for-dsls"></a>撰寫 Dsl MEF 擴充功能  
 您可以在個別的 DSL 擴充功能方案之組件程式碼專案中撰寫延伸模組。 您也可以在 DslPackage 專案中，使用 MEF，是為了方便撰寫命令、 手勢和驗證程式碼做為 DSL 的一部分。  
  
### <a name="menu-commands"></a>功能表命令  
 若要撰寫功能表命令，定義一個類別，實作<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>和前置詞在名為您的 DSL 中定義的屬性與類別*您的 Dsl*`CommandExtension`。</xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> 您可以撰寫一個以上的功能表命令類別。  
  
 `QueryStatus()`每當使用者以滑鼠右鍵按一下圖表會呼叫。 它應該檢查目前的選取範圍，並設定`command.Enabled`指出命令適用。  
  
```  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl; // My DSL  
using Company.MyDsl.ExtensionEnablement; // My DSL  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension  
  
namespace MyMefExtension  
{  
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:  
  [MyDslCommandExtension]   
  public class MyCommandClass : ICommandExtension  
  {   
    /// <summary>  
    /// Provides access to current document and selection.  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Called when the user selects this command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      // Transaction is required if you want to update elements.  
      using (Transaction t = SelectionContext.CurrentStore  
              .TransactionManager.BeginTransaction("fix names"))  
      {  
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)  
        {  
          ExampleElement element = shape.ModelElement as ExampleElement;  
          element.Name = element.Name + " !";  
        }  
        t.Commit();  
      }  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines whether the command should appear.  
    /// This method should set command.Enabled and command.Visible.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled =  
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines the text of the command in the menu.  
    /// </summary>  
    public string Text  
    {  
      get { return "My menu command"; }  
    }  
  }  
}  
  
```  
  
### <a name="gesture-handlers"></a>軌跡處理常式  
 軌跡處理常式可以處理物件的內部或外部從任何地方，拖曳到圖表上[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 下列範例會讓使用者可以將檔案從 Windows 檔案總管拖曳至圖表。 它會建立包含檔案名稱的項目。  
  
 您可以撰寫處理常式來處理來自其他 DSL 模型和 UML 模型的拖曳。 如需詳細資訊，請參閱[How to︰ 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。  
  
```  
  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;   
  
namespace MefExtension  
{  
  [MyDslGestureExtension]  
  class MyGestureExtension : IGestureExtension  
  {  
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
    {  
      System.Windows.Forms.MessageBox.Show("double click!");  
    }  
  
    /// <summary>  
    /// Called when the user drags anything over the diagram.  
    /// Return true if the dragged object can be dropped on the current target.  
    /// </summary>  
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>  
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>  
    /// <returns></returns>  
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      // This handler only allows items to be dropped onto the diagram:  
      return targetMergeElement is MefDsl2Diagram &&  
      // And only accepts files dragged from Windows Explorer:  
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");  
    }  
  
    /// <summary>  
    /// Called when the user drops an item onto the diagram.  
    /// </summary>  
    /// <param name="targetDropElement"></param>  
    /// <param name="diagramDragEventArgs"></param>  
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;  
      if (diagram == null) return;  
  
      // This handler only accepts files dragged from Windows Explorer:  
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];  
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;   
  
      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))  
      {  
        // Create an element to represent each file:  
        foreach (string fileName in draggedFileNames)  
        {  
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);  
          element.Name = fileName;  
  
          // This method of adding the new element allows the position  
          // of the shape to be specified:            
          ElementGroup group = new ElementGroup(element);  
          diagram.ElementOperations.MergeElementGroupPrototype(  
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
  
```  
  
### <a name="validation-constraints"></a>驗證條件約束  
 驗證方法會標示`ValidationExtension` <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>.</xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> DSL，並也會產生的屬性 此方法可以出現在屬性未標記的任何類別。  
  
 如需詳細資訊，請參閱[驗證定義域專屬語言](../modeling/validation-in-a-domain-specific-language.md)。  
  
```  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
namespace MefExtension  
{  
  class MyValidationExtension // Can be any class.  
  {  
    // SAMPLE VALIDATION METHOD.  
    // All validation methods have the following attributes.  
  
    // Specific to the extended DSL:  
    [MyDslValidationExtension]   
  
    // Determines when validation is applied:  
    [ValidationMethod(  
       ValidationCategories.Save  
     | ValidationCategories.Open  
     | ValidationCategories.Menu)]  
  
    /// <summary>  
    /// When validation is executed, this method is invoked  
    /// for every element in the model that is an instance  
    /// of the second parameter type.  
    /// </summary>  
    /// <param name="context">For reporting errors</param>  
    /// <param name="elementToValidate"></param>  
    private void ValidateClassNames  
      (ValidationContext context,  
       // Type determines to what elements this will be applied:  
       ExampleElement elementToValidate)  
    {   
      // Write code here to test values and links.  
      if (elementToValidate.Name.IndexOf(' ') >= 0)  
      {  
        // Log any unacceptable values:  
        context.LogError(  
          // Description:  
          "Name must not contain spaces"   
          // Error code unique to this type of error:  
          , "MyDsl001"   
          // Element to highlight when user double-clicks error:  
          , elementToValidate);   
} } } }  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed 的 Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [如何︰ 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [特定領域語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)
