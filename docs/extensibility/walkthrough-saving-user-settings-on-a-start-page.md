---
title: "逐步解說︰ 在起始頁面上儲存使用者設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>逐步解說︰ 在起始頁面上儲存使用者設定
您可以保存使用者設定起始頁。 按照本逐步解說，您可以建立當使用者按一下按鈕時，並接著會擷取該設定，每次啟動 頁面載入時，設定儲存至登錄的控制項。 起始頁專案範本包含可自訂的使用者控制項，以及預設啟動頁面 XAML 呼叫該控制項，因為您沒有修改 [啟動] 頁面本身。  
  
 本逐步解說中具現化的設定存放區是執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>介面，以便讀取和寫入呼叫時的下列登錄位置︰ HKCU\Software\Microsoft\VisualStudio\14.0\\*CollectionName* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 當正在執行中的 Visual Studio 的實驗執行個體時，設定存放區來讀取和寫入 HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*集合名稱。*  
  
 如需如何保存設定的詳細資訊，請參閱[擴充使用者設定和選項](../extensibility/extending-user-settings-and-options.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
> [!NOTE]
>  若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
>   
>  您可以使用下載的入門 頁面上的專案範本**擴充管理員**。  
  
## <a name="setting-up-the-project"></a>設定專案  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>若要設定在這個逐步解說專案  
  
1.  建立入門 頁面上的專案中所述[建立自訂起始頁](creating-a-custom-start-page.md)。 將專案命名為**SaveMySettings**。  
  
2.  在**方案總管 中**，加入下列組件參考加入 StartPageControl 專案︰  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  開啟 MyControl.xaml。  
  
4.  從 [XAML] 窗格中，在最上層<xref:System.Windows.Controls.UserControl>項目定義之後，加入下列事件宣告的命名空間宣告。</xref:System.Windows.Controls.UserControl>  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  在 [設計] 窗格中，按一下控制項的主要區域，然後按 DELETE 鍵。  
  
     這會移除<xref:System.Windows.Controls.Border>項目和它，而且只有最上層的分葉中的所有<xref:System.Windows.Controls.Grid>項目。</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.Border>  
  
6.  從**工具箱**，拖曳<xref:System.Windows.Controls.StackPanel>方格控制項。</xref:System.Windows.Controls.StackPanel>  
  
7.  現在，請將<xref:System.Windows.Controls.TextBlock>、 <xref:System.Windows.Controls.TextBox>，和一個按鈕為<xref:System.Windows.Controls.StackPanel>。</xref:System.Windows.Controls.StackPanel> </xref:System.Windows.Controls.TextBox> </xref:System.Windows.Controls.TextBlock>  
  
8.  新增**X:name**屬性<xref:System.Windows.Controls.TextBox>，和`Click`事件<xref:System.Windows.Controls.Button>，如下列範例所示。</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox>  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>實作使用者控制項  
  
#### <a name="to-implement-the-user-control"></a>若要實作使用者控制項  
  
1.  在 XAML 窗格中，以滑鼠右鍵按一下`Click`屬性<xref:System.Windows.Controls.Button>項目，然後再按一下 **巡覽至事件處理常式**。</xref:System.Windows.Controls.Button>  
  
     這會開啟 MyControl.xaml.cs，並建立虛設常式的處理常式`Button_Click`事件。  
  
2.  新增下列`using`陳述式加入檔案的頂端。  
  
     [!code-cs[StartPageDTE #&11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  加入私用`SettingsStore`屬性，如下列範例所示。  
  
    ```c#  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     這個屬性會先取得參考<xref:EnvDTE80.DTE2>介面，其中包含自動化物件模型中，從<xref:System.Windows.FrameworkElement.DataContext%2A>的使用者控制項，然後使用來取得執行個體的 DTE<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:System.Windows.FrameworkElement.DataContext%2A> </xref:EnvDTE80.DTE2> 然後它會傳回目前的使用者設定使用該執行個體。  
  
4.  填寫`Button_Click`事件，如下所示。  
  
    ```c#  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     這會將文字方塊的內容寫入登錄中的 「 MySettings 」 集合中的 「 MySetting 」 欄位。 如果集合不存在，則會建立它。  
  
5.  新增下列處理常式`OnLoaded`使用者控制項的事件。  
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     這會設定 「 MySetting 」 的目前值的文字方塊中的文字。  
  
6.  建立使用者控制項。  
  
7.  在**方案總管 中**，開啟 source.extension.vsixmanifest。  
  
8.  在資訊清單編輯器中，設定**產品名稱**至**儲存我的設定起始頁**。  
  
     這會將 [啟動] 頁面的名稱是出現在**自訂起始頁**清單中**選項**對話方塊。  
  
9. 建置 StartPage.xaml。  
  
## <a name="testing-the-control"></a>測試控制項  
  
#### <a name="to-test-the-user-control"></a>若要測試使用者控制項  
  
1.  按 F5。  
  
     Visual Studio 的實驗執行個體隨即開啟。  
  
2.  在實驗性的執行個體，在**工具**] 功能表上，按一下 [**選項**。  
  
3.  在**環境**節點中，按一下 **啟動**，然後在**自訂起始頁**清單中，選取**[安裝延伸模組] 儲存我的設定起始頁**。  
  
     按一下 [確定]。  
  
4.  若已開啟，然後在關閉 [啟動] 頁面**檢視**] 功能表上，按一下 [**起始頁**。  
  
5.  在 [啟動] 頁面中，按一下 [ **MyControl** ] 索引標籤。  
  
6.  在文字方塊中，輸入**Cat**，然後按一下 **儲存我的設定**。  
  
7.  關閉 [啟動] 頁面，然後再重新開啟它。  
  
     「 貓 」 這個字應該會顯示在文字方塊中。  
  
8.  「 貓 」 這個字取代成"Dog"這個字。 請勿按的按鈕。  
  
9. 關閉 [啟動] 頁面，然後再重新開啟它。  
  
     "Dog"這個字應該顯示在文字方塊中，即使未儲存的設定。 這是因為 Visual Studio 將工具視窗保留在記憶體中，即使它們已關閉，直到關閉 Visual Studio 本身。  
  
10. 關閉 Visual Studio 的實驗執行個體。  
  
11. 按 F5 以重新開啟的實驗執行個體。  
  
12. 「 貓 」 這個字應該會顯示在文字方塊中。  
  
## <a name="next-steps"></a>後續步驟  
 您可以修改此使用者控制項，來儲存和擷取任何數目的自訂設定來取得及設定使用不同的值，從不同的事件處理常式`SettingsStore`屬性。 只要您使用不同`propertyName`參數，每次呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>，值不會覆寫另一個在登錄中。</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [將 Visual Studio 命令加入至 [開始] 頁面](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
