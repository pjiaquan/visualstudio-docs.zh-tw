---
title: "將工具列新增至工具視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
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
ms.openlocfilehash: 80f8d2e3d689b05680c5d43a0d4b26f17d9a88ce
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>將工具列新增至工具視窗
本逐步解說示範如何將工具列新增至工具視窗。  
  
 工具列是水平或垂直的區域，其中包含繫結至命令的按鈕。 在工具視窗工具列的長度永遠是相同的寬度或高度的工具視窗中，根據在停駐工具列。  
  
 不同於在 IDE 中的工具列，工具列的工具視窗必須停駐而且無法移動或自訂。 如果 VSPackage umanaged 程式碼中撰寫，則可停駐工具列任何一邊上。  
  
 如需如何加入工具列的詳細資訊，請參閱[將工具列新增](../extensibility/adding-a-toolbar.md)。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>建立工具視窗工具列  
  
1.  建立 VSIX 專案，名為`TWToolbar`，具有名為這兩個功能表命令**TWTestCommand**和工具視窗，名為**TestToolWindow**。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)和[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。 您需要加入命令項目範本加入工具視窗範本之前。  
  
2.  在 TWTestCommandPackage.vsct，尋找 [符號] 區段。 在名為 guidTWTestCommandPackageCmdSet GuidSymbol 節點可以宣告一個工具列和工具列群組，如下所示。  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  在頂端`Commands`區段中，建立`Menus`一節。 新增`Menu`項目來定義工具列。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     工具列不可為巢狀，像是子功能表。 因此，您沒有指定父代。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 一般而言，工具列的初始位置以程式設計方式定義，但使用者的後續變更會保存。  
  
4.  在 [群組] 區段中，定義一個群組包含工具列命令。  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  在 [按鈕] 區段中，變更現有 Button 元素的父代為工具列群組，讓工具列會顯示。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     根據預設，如果工具列沒有任何命令，它不會出現。  
  
     因為新的工具列不會自動加入至 [工具] 視窗中，必須明確地新增工具列。 下一節將討論這個部分。  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>將工具列新增至 [工具] 視窗  
  
1.  TWTestCommandPackageGuids.cs 中新增下列程式碼行。  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  TestToolWindow.cs 中新增下列 using 陳述式。  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  TestToolWindow 建構函式中加入下列這一行。  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>在 [工具] 視窗中測試工具列  
  
1.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。  
  
2.  在**檢視 / 其他視窗**] 功能表上，按一下 [**測試工具視窗**顯示 [工具] 視窗。  
  
     您應該會看到 （看起來像預設圖示） 在頂端工具列方的 [工具] 視窗標題的正下方。  
  
3.  在工具列上，按一下圖示以顯示訊息**TWTestCommandPackage 內 TWToolbar.TWTestCommand.MenuItemCallback()**。  
  
## <a name="see-also"></a>另請參閱  
 [新增工具列](../extensibility/adding-a-toolbar.md)
