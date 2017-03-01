---
title: "將工具列新增 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
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
ms.openlocfilehash: e6b9b6a5ce384112464d0f768c35bf7b5c57a589
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar"></a>新增工具列
此逐步解說示範如何將工具列新增至 Visual Studio IDE。  
  
 工具列是水平或垂直的區域，其中包含繫結至命令的按鈕。 根據其實作，在 IDE 中的工具列都可以重新定位、 停駐在任何一側的主要 IDE 視窗中，或對保持在其他視窗的前面。  
  
 此外，使用者可以將命令加入至工具列，或移除它們，方法是使用**自訂**對話方塊。 一般而言，工具列 VSPackages 是使用者自訂。 IDE 會處理所有自訂項目，並且 VSPackage 回應命令。 VSPackage 不必知道命令實體所在的位置。  
  
 如需功能表的詳細資訊，請參閱[命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>使用工具列建立擴充功能  
 建立 VSIX 專案，名為`IDEToolbar`。 加入名為功能表命令項目範本**ToolbarTestCommand**。 如需如何執行這項操作，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Ide 建立工具列  
  
1.  在 ToolbarTestCommandPackage.vsct，尋找 [符號] 區段。 在名為 guidToolbarTestCommandPackageCmdSet GuidSymbol 元素中，將宣告，新增工具列和工具列群組，如下所示。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  在命令 > 一節的最上方，建立功能表一節。 將功能表項目加入至 [功能表] 區段，以定義您的工具列。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     工具列不可為巢狀，像是子功能表。 因此，您沒有指定父群組。 此外，您不需要設定優先順序，因為使用者可以移動工具列。 一般而言，工具列的初始位置以程式設計方式定義，但使用者的後續變更會保存。  
  
3.  在[群組](../extensibility/groups-element.md) 區段中，在現有的群組項目之後定義[群組](../extensibility/group-element.md)項目來包含工具列命令。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  請在工具列上顯示的按鈕。 在 [按鈕] 區段中，來取代父代中的區塊至工具列按鈕。 結果的按鈕區塊看起來應該像這樣︰  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     根據預設，如果工具列沒有任何命令，它不會出現。  
  
5.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
6.  以滑鼠右鍵按一下 Visual Studio 功能表列，以取得工具列的清單。 選取**測試工具列**。  
  
7.  您會看到您的工具列圖示右邊的 檔案 圖示中尋找。 當您按一下圖示時，您應該會看到訊息方塊，指出**ToolbarTestCommandPackage。內部 IDEToolbar.ToolbarTestCommand.MenuItemCallback()**。  
  
## <a name="see-also"></a>另請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
