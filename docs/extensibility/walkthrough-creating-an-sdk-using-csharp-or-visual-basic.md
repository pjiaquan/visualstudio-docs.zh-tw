---
title: "逐步解說︰ 建立使用 C# 或 Visual Basic SDK |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 20
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
ms.sourcegitcommit: c43f3022ba53e67ff510ed63aa419c9f23964a58
ms.openlocfilehash: ce17214ec4bfc49f82ee537d6dee13a471a36ca2
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>逐步解說︰ 建立使用 C# 或 Visual Basic 的 SDK
在此逐步解說中，您將學習如何使用 Visual C# 中建立簡單的數學程式庫 SDK，然後再封裝 SDK 為 Visual Studio 擴充功能 (VSIX)。 您將完成下列程序︰  
  
-   [若要建立 SimpleMath Windows 執行階段元件](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [若要建立 SimpleMathVSIX 擴充功能專案](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [若要建立範例應用程式使用類別庫](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>若要建立 SimpleMath Windows 執行階段元件  
  
1.  在功能表列上選擇 **檔案**，**新增**，**新的專案**。  
  
2.  在範本清單中，展開**Visual C#**或**Visual Basic**，選擇  **Windows 市集**節點，然後選擇  **Windows 執行階段元件**範本。  
  
3.  在**名稱**方塊中，指定**SimpleMath**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案節點，然後按一下**屬性**。  
  
5.  重新命名**Class1.cs**至**Arithmetic.cs**並進行更新以符合下列程式碼︰  
  
     [!code-cs[CreatingAnSDKUsingWinRT&#3;](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs) ] 
     [!code-vb [CreatingAnSDKUsingWinRT&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  在**方案總管] 中**，開啟捷徑功能表**方案 'SimpleMath'**節點，然後選擇 [ **Configuration Manager**。  
  
     **Configuration Manager**對話方塊隨即開啟。  
  
7.  在**作用中方案組態**清單中，選擇**版本**。  
  
8.  在**組態**資料行中，確認**SimpleMath**資料列設為**版本**，然後選擇 [**關閉**] 按鈕以接受變更。  
  
    > [!IMPORTANT]
    >  SimpleMath 元件 SDK 包含只有一個組態。 此設定必須是發行的組建，或使用元件的應用程式將不會通過憑證[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]。  
  
9. 在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案節點，然後按一下**建置**。  
  
##  <a name="a-namecreatevsixa-to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>若要建立 SimpleMathVSIX 擴充功能專案  
  
1.  在捷徑功能表上**方案 'SimpleMath'**節點，選擇**新增**，**新的專案**。  
  
2.  在範本清單中，展開**Visual C#**或**Visual Basic**，選擇 **擴充性**節點，然後選擇  **VSIX 專案**範本。  
  
3.  在**名稱**方塊中，指定**SimpleMathVSIX**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管] 中**，選擇 [ **source.extension.vsixmanifest**項目。  
  
5.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
6.  以下列 XML 取代現有的 XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT #&1;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  在**方案總管] 中**，選擇 [ **SimpleMathVSIX**專案。  
  
8.  在功能表列上選擇 **專案**，**加入新項目**。  
  
9. 在清單中**一般項目**，依序展開**資料**，然後選擇  **XML 檔案**。  
  
10. 在**名稱**方塊中，指定`SDKManifest.xml`，然後選擇 [**新增**] 按鈕。  
  
11. 在**方案總管 中**，開啟捷徑功能表`SDKManifest.xml`，選擇**屬性**，然後將變更的值**Include in VSIX**屬性**True**。  
  
12. 以下列 XML 取代檔案的內容：  

    **C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. 在**方案總管 中**，開啟捷徑功能表**SimpleMathVSIX**專案中，選擇 **新增**，然後選擇 **新資料夾**。  
  
14. 若要將資料夾重新命名`references`。  
  
15. 開啟捷徑功能表**參考**資料夾中，選擇 **新增**，然後選擇 **新資料夾**。  
  
16. 重新命名的子資料夾`commonconfiguration`，建立的子資料夾中，並將子資料夾`neutral`。  
  
17. 重複上述四個步驟，重新命名的第一個資料夾，以這次`redist`。  
  
     專案現在會包含下列資料夾結構︰  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. 在**方案總管 中**，開啟捷徑功能表**SimpleMath**專案，然後再選擇**在檔案總管 中開啟資料夾**。  
  
19. 在**檔案總管**、 瀏覽至 bin\debug 資料夾、 開啟 SimpleMath.winmd 檔案的捷徑功能表，然後選擇**複製**。  
  
20. 在**方案總管 中**，將檔案貼到 references\commonconfiguration\neutral 資料夾**SimpleMathVSIX**專案。  
  
21. 重複上述步驟，將 SimpleMath.pri 檔案貼到 [redist\commonconfiguration\neutral] 資料夾中**SimpleMathVSIX**專案。  
  
22. 在**方案總管] 中**，選擇 [ **SimpleMath.winmd**。  
  
23. 在功能表列上選擇 **檢視**，**屬性**(鍵盤︰ 選擇 F4 鍵)。  
  
24. 在**屬性** 視窗中，變更**建置動作**屬性**內容**，然後變更**Include in VSIX**屬性**True**。  
  
25. 在**方案總管 中**，重複此程序**SimpleMath.pri**。  
  
26. 在**方案總管] 中**，選擇 [ **SimpleMathVSIX**專案。  
  
27. 在功能表列上選擇 **建置**，**建置 SimpleMathVSIX**。  
  
28. 在**方案總管 中**，開啟捷徑功能表**SimpleMathVSIX**專案，然後再選擇**在檔案總管 中開啟資料夾**。  
  
29. 在**檔案總管**，瀏覽至 \bin\Release 資料夾，然後再執行 SimpleMathVSIX.vsix 安裝它。  
  
30. 選擇**安裝** 按鈕，等候安裝完成，然後再重新啟動 Visual Studio。  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>若要建立範例應用程式使用類別庫  
  
1.  在功能表列上選擇 **檔案**，**新增**，**新的專案**。  
  
2.  在範本清單中，展開**Visual C#**或**Visual Basic**，然後選擇  **Windows 市集**節點。  
  
3.  選擇**空白應用程式**範本，將專案**ArithmeticUI**，然後選擇 [**確定**] 按鈕。  
  
4.  在**方案總管 中**，開啟捷徑功能表**ArithmeticUI**專案，然後再選擇**新增**，**參考**。  
  
5.  在參考型別清單中，展開**Windows**，然後選擇 **延伸**。  
  
6.  在詳細資料窗格中，選擇 **簡單數學 SDK**延伸模組。  
  
     您的 SDK 的其他資訊隨即顯示。 您可以選擇**更多資訊**開啟 http://www.msdn.microsoft.com，如您稍早在本逐步解說 SDKManifest.xml 檔案中所指定的連結。  
  
7.  在**參考管理員**對話方塊中，選取**簡單數學 SDK**核取方塊，然後按一下**確定** 按鈕。  
  
8.  在功能表列上選擇 **檢視**，**物件瀏覽器**。  
  
9. 在**瀏覽**清單中，選擇**簡單的數學**。  
  
     您現在可以瀏覽 SDK 的功能。  
  
10. 在**方案總管 中**，開啟 MainPage.xaml，並將其內容取代下列 XAML:  

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. 更新 MainPage.xaml.cs 以符合下列程式碼︰  
  
     [!code-cs[CreatingAnSDKUsingWinRTDemoApp&#2;](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs) ] 
     [!code-vb [CreatingAnSDKUsingWinRTDemoApp&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. 選擇 F5 鍵以執行應用程式。  
  
13. 在應用程式中，輸入任何兩個數字，並選擇了作業，然後選擇** = **  按鈕。  
  
     正確的結果會出現。  
  
 您已成功建立和使用擴充功能 SDK。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 建立使用 c + + 的 SDK](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [逐步解說︰ 建立使用 JavaScript 的 SDK](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [建立軟體開發套件](../extensibility/creating-a-software-development-kit.md)
