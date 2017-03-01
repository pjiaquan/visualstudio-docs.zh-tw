---
title: "建立和管理強制回應對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1bb0372ab217847f91b1cdeeb8cf2915379e2f66
ms.lasthandoff: 02/22/2017

---
# <a name="creating-and-managing-modal-dialog-boxes"></a>建立和管理強制回應對話方塊
當您建立 Visual Studio 中的強制回應對話方塊時，您必須確定當出現對話方塊時，對話方塊中的父視窗已停用，然後在對話方塊關閉之後，重新啟用父視窗。 如果不這麼做，您可能會收到錯誤: 「 Microsoft Visual Studio 無法因為關閉強制回應對話方塊正在使用中。 關閉使用中的對話方塊並再試一次 」。  
  
 有兩個方法可以做到。 建議的方式，如果您有 WPF 對話方塊中，會從它衍生出來<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，然後呼叫<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>以顯示對話方塊。</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 如果您這樣做，您不需要管理父視窗的強制回應狀態。  
  
 如果您的對話方塊不是 WPF，或某些其他原因，您不能衍生您的對話方塊類別從<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，則您必須取得對話方塊中的父代藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>自行並管理強制回應狀態，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>方法，以 0 (false)，然後再顯示對話方塊，並關閉對話方塊後呼叫一次與參數 1 (true) 方法的參數。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>建立對話方塊衍生自 DialogWindow  
  
1.  建立 VSIX 專案，名為**OpenDialogTest** ，並新增名為功能表命令**OpenDialog**。 如需如何執行這項操作的詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>類別，則必須加入下列組件的參考 (在 [架構] 索引標籤的**加入參考**對話方塊):</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  在 OpenDialog.cs，新增下列`using`陳述式︰  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  宣告類別，名為**TestDialogWindow**衍生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>::</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  若要能夠最小化和最大化 對話方塊中，設定<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>和<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>設為 true:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法，將現有的程式碼取代為下列︰  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  建置並執行應用程式。 Visual Studio 的實驗執行個體應該會出現。 在**工具**的實驗執行個體 功能表中您應該會看到名為命令**叫用 OpenDialog**。 當您按一下此命令時，您應該會看到對話方塊視窗。 您應該能夠降至最低，並將視窗最大化。  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>建立和管理不是衍生自 DialogWindow 對話方塊  
  
1.  您可以使用此程序， **OpenDialogTest**您在相同的組件參考的上一個程序中建立的方案。  
  
2.  新增下列`using`宣告︰  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  建立一個名為**TestDialogWindow2**衍生自<xref:System.Windows.Window>::</xref:System.Windows.Window>  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  加入私用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>參考  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  新增設定對<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>::</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>參考的建構函式  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法，將現有的程式碼取代為下列︰  
  
    ```c#  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  建置並執行應用程式。 在**工具**功能表您應該會看到名為命令**叫用 OpenDialog**。 當您按一下此命令時，您應該會看到對話方塊視窗。
