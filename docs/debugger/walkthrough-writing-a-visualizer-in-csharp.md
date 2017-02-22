---
title: "逐步解說：在 C# 中撰寫視覺化檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "視覺化檢視, 撰寫"
  - "逐步解說 [Visual Studio], 視覺化檢視"
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 逐步解說：在 C# 中撰寫視覺化檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說會示範如何使用 C\# 撰寫簡易的視覺化檢視。  您在本逐步解說中建立的視覺化檢視，會使用 Windows Form 訊息方塊顯示字串的內容。  這個簡易的字串視覺化檢視本身雖然不是特別實用，但是它說明了在為其他資料型別建立更有用的視覺化檢視時，所須遵循的基本步驟。  
  
> [!NOTE]
>  根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中所描述的不同。  若要變更設定，請在 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 視覺化檢視的程式碼必須放置在 DLL 中，由偵錯工具進行讀取。  因此，第一步就是為 DLL 建立類別庫 \(Class Library\) 專案。  
  
#### 若要建立類別庫專案  
  
1.  在 \[**檔案**\] 功能表上，選擇 \[**新增**\]，然後按一下 \[**新增專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 下，選擇 \[**Visual C\#**\]。  
  
3.  在 \[**範本**\] 方塊中，選擇 \[**類別庫**\]。  
  
4.  在 \[**名稱**\] 方塊中，為該類別庫輸入適當的名稱，例如 MyFirstVisualizer。  
  
5.  按一下 \[**確定**\]。  
  
 建立類別庫之後，必須加入 Microsoft.VisualStudio.DebuggerVisualizers.DLL 的參考，如此您才能使用這個位置中定義的類別。  但是在加入參考之前，您必須重新命名一些類別，使它們擁有有意義的名稱。  
  
#### 若要重新命名 Class1.cs 並加入 Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[Class1.cs\]，然後在捷徑功能表中選擇 \[**重新命名**\]。  
  
2.  將 Class1.cs 變更成有意義的名稱，例如 DebuggerSide.cs。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 DebuggerSide.cs 中的類別宣告，以符合新的檔案名稱。  
  
3.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**參考**\]，然後在捷徑功能表中按一下 \[**加入參考**\]。  
  
4.  在 \[**加入參考**\] 對話方塊的 \[**.NET**\] 索引標籤上，選擇 \[Microsoft.VisualStudio.DebuggerVisualizers.DLL\]。  
  
5.  按一下 \[**確定**\]。  
  
6.  在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 現在，您已經準備好可以建立偵錯工具端的程式碼。  這是在偵錯工具內執行的程式碼，用以顯示您要視覺化的資訊。  首先，您必須變更 `DebuggerSide` 物件的宣告，使其繼承基底類別 `DialogDebuggerVisualizer`。  
  
#### 若要繼承自 DialogDebuggerVisualizer  
  
1.  在 DebuggerSide.cs 中，移至下列程式碼行：  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  將程式碼變更為：  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` 含有一個您必須覆寫的抽象方法 \(`Show`\)。  
  
#### 若要覆寫 DialogDebuggerVisualizer.Show 方法  
  
-   在 `public class DebuggerSide` 中，加入下列**方法**：  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show` 方法中包含實際建立視覺化檢視對話方塊或其他使用者介面的程式碼，並會在偵錯工具中顯示已傳遞至視覺化檢視的資訊。  您必須加入該程式碼，以建立對話方塊並顯示資訊。  在本逐步解說中，您將使用 Windows Form 訊息方塊進行上述動作。  首先，您必須加入參考和 System.Windows.Forms `using` 陳述式。  
  
#### 若要加入 System.Windows.Forms  
  
1.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**參考**\]，然後在捷徑功能表中按一下 \[**加入參考**\]。  
  
2.  在 \[**加入參考**\] 對話方塊的 \[**.NET**\] 索引標籤中，選擇 System.Windows.Forms.DLL。  
  
3.  按一下 \[**確定**\]。  
  
4.  在 DebuggerSide.cs 中，將下列陳述式加入至 `using` 陳述式：  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 現在，您可以加入某些程式碼，建立並顯示視覺化檢視的使用者介面。  由於這是您的第一個視覺化檢視，因此我們盡量簡化使用者介面，並且會使用訊息方塊。  
  
#### 若要在對話方塊中顯示視覺化檢視輸出  
  
1.  在 `Show` 方法中，加入下列程式碼行：  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     這個程式碼範例不包括錯誤處理。  在真實的視覺化檢視或其他任何類型的應用程式中，都應該包括錯誤處理功能。  
  
2.  在 \[**建置**\] 功能表上，選擇 \[**建置 MyFirstVisualizer**\]。  專案應該會順利建置。  在繼續進行之前，請更正任何建置錯誤。  
  
 這是偵錯工具端程式碼的結尾。  但是還有一個步驟，就是加入告知偵錯項目端構成視覺化檢視類別集合的屬性。  
  
#### 若要加入偵錯項目端程式碼  
  
1.  將下列屬性程式碼加入至 DebuggerSide.cs，放置在 `using` 陳述式之後，`namespace MyFirstVisualizer` 之前：  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  在 \[**建置**\] 功能表上，選擇 \[**建置 MyFirstVisualizer**\]。  專案應該會順利建置。  在繼續進行之前，請更正任何建置錯誤。  
  
 這時，您的第一個視覺化檢視已完成。  如果您正確遵循這些步驟的話，應該能夠建置視覺化檢視，並將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  但是，在將視覺化檢視安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之前，應該先進行測試以確定它能正確執行。  現在，您將建立 Test Harness 來執行這個視覺化檢視，而不將它安裝至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中。  
  
#### 若要加入顯示視覺化檢視的測試方法  
  
1.  將下列方法加入至 `public DebuggerSide` 類別：  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  在 \[**建置**\] 功能表上，選擇 \[**建置 MyFirstVisualizer**\]。  專案應該會順利建置。  在繼續進行之前，請更正任何建置錯誤。  
  
 接下來，您必須建立可執行的專案，以呼叫視覺化檢視的 DLL。  為求簡化起見，我們將使用主控台應用程式專案。  
  
#### 若要將主控台應用程式專案加入至方案  
  
1.  在 \[**檔案**\] 功能表上，選擇 \[**加入**\]，然後按一下 \[**新增專案**\]。  
  
2.  在 \[**加入新的專案**\] 對話方塊的 \[**範本**\] 方塊中，選擇 \[**主控台應用程式**\]。  
  
3.  在 \[**名稱**\] 方塊中，為主控台應用程式輸入有意義的名稱，例如 `MyTestConsole`。  
  
4.  按一下 \[**確定**\]。  
  
 此時，你必須加入必要的參考，如此 MyTestConsole 才能呼叫 MyFirstVisualizer。  
  
#### 若要將必要參考加入至 MyTestConsole  
  
1.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**MyTestConsole**\]，然後在捷徑功能表中選擇 \[**加入參考**\]。  
  
2.  在 \[**加入參考**\] 對話方塊的 \[**.NET**\] 索引標籤中，選擇 \[Microsoft.VisualStudio.DebuggerVisualizers.DLL\]。  
  
3.  按一下 \[**確定**\]。  
  
4.  以滑鼠右鍵按一下 \[**MyTestConsole**\]，然後再次選擇 \[**加入參考**\]。  
  
5.  在 \[**加入參考**\] 對話方塊中，按一下 \[**專案**\] 索引標籤，然後按一下 \[MyFirstVisualizer\]。  
  
6.  按一下 \[**確定**\]。  
  
 現在，您就可以加入程式碼來完成 Test Harness。  
  
#### 若要將程式碼加入至 MyTestConsole  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[Program.cs\]，然後在捷徑功能表中選擇 \[**重新命名**\]。  
  
2.  將 Program.cs 編輯成比較有意義的名稱，例如 TestConsole.cs。  
  
     **注意事項** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動變更 TestConsole.cs 中的類別宣告，以符合新的檔案名稱。  
  
3.  在 TestConsole.cs 中，將下列程式碼加入至 `using` 陳述式中：  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  在 `Main` 方法中，加入下列程式碼：  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 現在，您可以準備測試第一個視覺化檢視。  
  
#### 若要測試視覺化檢視  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**MyTestConsole**\]，然後從捷徑功能表中選擇 \[**設定為啟始專案**\]。  
  
2.  在 \[**偵錯**\] 功能表上選擇 \[**啟動**\]。  
  
     主控台應用程式隨即啟動，而且視覺化檢視會出現，顯示 "Hello, World" 字串。  
  
 恭喜您！  您已完成建置和測試第一個視覺化檢視。  
  
 如果您想在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用視覺化檢視，而不只是從測試控管中進行呼叫，就必須安裝該視覺化檢視。  如需詳細資訊，請參閱[如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)。  
  
## 使用視覺化檢視項目範本  
 到目前為止，這個逐步解說示範了如何手動建立視覺化檢視。  這是以實習的方式進行。  既然您已經了解簡單的視覺化檢視是如何運作的，那麼接下來建立視覺化檢視的方法將更為簡便，也就是使用視覺化檢視項目範本。  
  
 首先，您必須建立新的類別庫專案。  
  
#### 若要建立新的類別庫  
  
1.  在 \[**檔案**\] 功能表上，選擇 \[**加入**\]，然後按一下 \[**新增專案**\]。  
  
2.  在 \[**加入新的專案**\] 對話方塊的 \[**專案類型**\] 下，選擇 \[**Visual C\#**\]。  
  
3.  在 \[**範本**\] 方塊中，選擇 \[**類別庫**\]。  
  
4.  在 \[**名稱**\] 方塊中，為該類別庫輸入適當的名稱，例如 MySecondVisualizer。  
  
5.  按一下 \[**確定**\]。  
  
 現在，您可以加入視覺化檢視項目：  
  
#### 若要加入視覺化檢視項目  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[MySecondVisualizer\]。  
  
2.  在捷徑功能表上，選擇 \[**加入**\]，然後按一下 \[**新增項目**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中的 \[**範本**\] 下方，於 \[**Visual Studio 安裝的範本**\] 中選取 \[**偵錯工具視覺化檢視**\]。  
  
4.  在 \[**名稱**\] 方塊中輸入適當的名稱，例如 SecondVisualizer.cs。  
  
5.  按一下 \[**加入**\]。  
  
 就是這樣，簡單明瞭！  請查看 SecondVisualizer.cs 檔案，並檢視範本為您加入的程式碼。  請繼續進行，並使用程式碼自行學習。  現在，您已經了暸解基本概念，便可以繼續自行建立更複雜且更實用的視覺化檢視。  
  
## 請參閱  
 [視覺化檢視架構](../debugger/visualizer-architecture.md)   
 [如何：安裝視覺化檢視](../debugger/how-to-install-a-visualizer.md)   
 [視覺化檢視](../debugger/create-custom-visualizers-of-data.md)