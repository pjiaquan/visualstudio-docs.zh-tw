---
title: "建立 Windows Form 工具箱控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 770963e06655c0d4da2946fa7981fd1e4496b7f0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-toolbox-control"></a>建立 Windows Form 工具箱控制項
Windows Form 工具箱控制項項目範本隨附於 Visual Studio 擴充性工具 (VS SDK) 中可讓您建立的控制項，會自動加入至**工具箱**時安裝延伸模組。 本主題說明如何使用範本來建立簡單的計數器控制項，您就可以散發給其他使用者。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>建立 Windows Form 工具箱控制項  
 Windows Form 工具箱控制項範本會建立未定義的使用者控制項，並提供的所有功能，才能將控制項加入至**工具箱**。  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>使用 Windows Form 工具箱控制項中建立的擴充功能  
  
1.  建立 VSIX 專案，名為`MyWinFormsControl`。 您可以找到 VSIX 專案範本，在**新的專案**下的對話方塊**Visual C# / 擴充性**。  
  
2.  專案開啟時，加入**Windows Form 工具箱控制項**項目範本名為`Counter`。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**加入 / 新的項目**。 在**加入新項目** 對話方塊中，移至**Visual C# / 擴充性**，然後選取**Windows Form 工具箱控制項**  
  
3.  這會新增使用者控制項， `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>要放置在控制項**工具箱**，和**Microsoft.VisualStudio.ToolboxControl**資產部署的 VSIX 資訊清單中的項目。</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
### <a name="building-a-user-interface-for-the-control"></a>建置控制項的使用者介面  
 `Counter`控制項需要兩個的子控制項︰<xref:System.Windows.Forms.Label>以顯示目前的計數和<xref:System.Windows.Forms.Button>計數重設為 0。</xref:System.Windows.Forms.Button> </xref:System.Windows.Forms.Label> 需要其他的子控制項，因為呼叫端將會以程式設計方式遞增計數器。  
  
##### <a name="to-build-the-user-interface"></a>建置使用者介面  
  
1.  在**方案總管 中**，連按兩下 Counter.cs 在設計工具中開啟它。  
  
2.  移除 「 按一下這裡 ！ 」 **按鈕**，預設會包含當您將加入 Windows Form 工具箱控制項項目範本。  
  
3.  從**工具箱**，拖曳`Label`控制項，然後`Button`其下的控制項至設計介面。  
  
4.  調整 150 整體使用者控制項的大小、 50 像素為單位，並調整大小的按鈕控制項為 50，20 像素。  
  
5.  在**屬性** 視窗中，設定下列值在設計介面上的控制項。  
  
    |控制項|屬性|值|  
    |-------------|--------------|-----------|  
    |`Label1`|**文字**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**文字**|重設|  
  
### <a name="coding-the-user-control"></a>編碼使用者控制項  
 `Counter` 控制項會公開遞增計數器的方法、計數器每次遞增所引發的事件、 `Reset` 按鈕、儲存目前計數的三個屬性、顯示文字，以及要顯示或隱藏 `Reset` 按鈕。 `ProvideToolboxControl`屬性會決定在何處**工具箱**`Counter`控制項將會出現。  
  
##### <a name="to-code-the-user-control"></a>使用者控制項的程式碼  
  
1.  按兩下表單，以開啟其 load 事件處理常式的程式碼視窗。  
  
2.  上述事件處理常式方法中，在控制項類別建立要儲存的計數器值和字串來儲存顯示的文字，如下列範例所示的整數。  
  
    ```c#  
    int currentValue;  
    string displayText;  
    ```  
  
3.  建立下列公用屬性宣告。  
  
    ```c#  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     呼叫端可以存取這些屬性，以取得及設定此計數器的顯示文字，以顯示或隱藏`Reset` 按鈕。 呼叫者可以取得目前的唯讀值`Value`屬性，但是不能值直接設定。  
  
4.  下列程式碼置於`Load`控制項的事件。  
  
    ```c#  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     設定**標籤**中的文字<xref:System.Windows.Forms.UserControl.Load>事件可讓套用它們的值之前載入的目標屬性。</xref:System.Windows.Forms.UserControl.Load> 設定**標籤**建構函式中的文字會導致空**標籤**。  
  
5.  建立下列公用方法，並遞增計數器。  
  
    ```c#  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  新增宣告`Incremented`控制項類別的事件。  
  
    ```c#  
    public event EventHandler Incremented;  
    ```  
  
     呼叫端可以新增處理常式，此事件以回應變更計數器的值。  
  
7.  返回 [設計] 檢視，然後按兩下`Reset`按鈕，以產生`btnReset_Click`事件處理常式，然後在下列範例所示填入。  
  
    ```c#  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  正上方類別定義，在`ProvideToolboxControl`屬性宣告中，從第一個參數的值變更`"MyWinFormsControl.Counter"`到`"General"`。 這會設定主控 [工具箱] 控制項的項目群組名稱。  
  
     下列範例會顯示 `ProvideToolboxControl` 屬性和調整過的類別定義。  
  
    ```c#  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>測試控制項  
 若要測試**工具箱**控制，先在開發環境中進行測試，然後編譯的應用程式。  
  
##### <a name="to-test-the-control"></a>測試控制項  
  
1.  按 F5。  
  
     這會建置專案，並開啟已安裝控制項的 Visual Studio 的第二個實驗性執行個體。  
  
2.  在 Visual Studio 的實驗執行個體，建立**Windows Form 應用程式**專案。  
  
3.  在**方案總管 中**，連按兩下以開啟設計工具中，如果它尚未開啟 Form1.cs。  
  
4.  在**工具箱**、`Counter`控制項應該顯示在**一般**一節。  
  
5.  拖放到`Counter`控制項加入表單，並加以選取。 `Value`， `Message`，和`ShowReset`屬性會顯示在**屬性** 視窗中，搭配都繼承自<xref:System.Windows.Forms.UserControl>.</xref:System.Windows.Forms.UserControl>的內容  
  
6.  將 `Message` 屬性設定為 `Count:`。  
  
7.  拖放到<xref:System.Windows.Forms.Button>控制項至表單，並將按鈕的名稱與文字屬性`Test`。</xref:System.Windows.Forms.Button>  
  
8.  按兩下這個按鈕，程式碼檢視中開啟 Form1.cs，並建立 click 處理常式。  
  
9. 在 click 處理常式呼叫`counter1.Increment()`。  
  
10. 在建構函式，呼叫之後`InitializeComponent`，型別`counter1``.``Incremented +=`然後按 TAB 鍵兩次。  
  
     Visual Studio 產生的表單層級處理常式`counter1.Incremented`事件。  
  
11. 反白顯示`Throw`事件處理常式，型別中的陳述式`mbox`，然後按兩次，從 mbox 程式碼片段中產生的訊息方塊的 TAB 鍵。  
  
12. 在下一行中，新增下列`if` / `else`區塊來設定可見性的`Reset` 按鈕。  
  
    ```c#  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. 按 F5。  
  
     開啟的表單。 `Counter`控制項會顯示下列文字。  
  
     **計數︰ 0**  
  
14. 按一下 [測試] 。  
  
     計數器增量和 Visual Studio 會顯示訊息方塊。  
  
15. 關閉訊息方塊。  
  
     **重設**按鈕就會消失。  
  
16. 按一下 **測試**直到計數器到達**5**關閉訊息方塊，每次。  
  
     **重設**按鈕會再度出現。  
  
17. 按一下 [重設] 。  
  
     此計數器會重設為**0**。  
  
## <a name="next-steps"></a>後續步驟  
 當您建置 [工具箱]  控制項時，Visual Studio 會在專案的 \bin\debug\ 資料夾中建立名為 *ProjectName*.vsix 的檔案。 您可以將 .vsix 檔案上傳到到網路或網站以部署控制項。 當使用者開啟.vsix 檔案時，安裝及新增至 Visual Studio 控制項**工具箱**在使用者電腦上。 或者，您可以上傳至.vsix 檔[Visual Studio 元件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，讓使用者可以藉由瀏覽以尋找它**工具 / 擴充功能和更新** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 [工具箱]](../misc/extending-the-toolbox.md)   
 [建立 WPF 工具箱控制項](../extensibility/creating-a-wpf-toolbox-control.md)   
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows Form 控制項開發的基本概念](http://msdn.microsoft.com/Library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
