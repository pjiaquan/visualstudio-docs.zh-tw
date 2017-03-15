---
title: "將功能表命令的當地語系化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
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
ms.openlocfilehash: 869a1c878a591e6b755fc1311132e159d38ffe8f
ms.lasthandoff: 02/22/2017

---
# <a name="localizing-menu-commands"></a>當地語系化的功能表命令
當地語系化的文字提供功能表和工具列建立當地語系化的.vsct 檔的命令和當地語系化的.resx 檔的 VSPackage，然後再更新專案檔的變更。  
  
 如需如何當地語系化安裝體驗的詳細資訊，請參閱[當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)。  
  
## <a name="localizing-command-names"></a>當地語系化的命令名稱  
 在 Vspackage 中，功能表命令和工具列按鈕是.vsct 檔中定義的。  
  
1.  在**方案總管 中**，變更從.vsct 檔的名稱*filename*至.vsct*檔名*.en US.vsct。  
  
2.  建立一份*filename*.en-US.vsct 每個當地語系化語言。  
  
     將每個複本*filename*。*地區設定*.vsct，其中*地區設定*是特定文化特性名稱。 如需文化特性名稱值的清單，請參閱[由 Microsoft 指派的地區設定識別碼](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx)。  
  
     這些*filename*。*地區設定*.vsct 檔會包含當地語系化的功能表文字，為您的封裝。  
  
3.  開啟每一個*filename*。*地區設定*.vsct 檔當地語系化文字。  
  
    1.  修改[ButtonText](../extensibility/buttontext-element.md)值為適合特定語言的元素。  
  
    2.  如果您將會提供當地語系化的圖示，修改[點陣圖](../extensibility/bitmap-element.md)值以指向目標檔案。  
  
     下列範例會顯示英文和西班牙文的開啟系列樹狀結構總管工具視窗的命令按鈕文字。  
  
     [FamilyTree.en US.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Family Tree Explorer</ButtonText>  
      </Strings>  
    </Button>  
    ```  
  
     [FamilyTree.es ES.vsct]  
  
    ```xml  
    <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">  
      <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
      <Icon guid="guidImages" id="bmpPic2" />  
      <Strings>  
        <CommandName>cmdidFamilyTree</CommandName>  
        <ButtonText>Explorar el arbol genealogico</ButtonText>  
      </Strings>  
    </Button>  
  
    ```  
  
## <a name="localizing-other-text-resources"></a>將其他文字資源當地語系化  
 資源 (.resx) 檔案中定義的文字命令名稱以外的資源。  
  
1.  重新命名 VSPackage.en US.resx VSPackage.resx。  
  
2.  每個當地語系化語言的 VSPackage.en US.resx 檔案的副本。  
  
     將每個複本 VSPackage。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
3.  重新命名 Resources.en US.resx Resources.resx。  
  
4.  每個當地語系化語言的 Resources.en US.resx 檔案的副本。  
  
     將每個複本的資源。*地區設定*.resx，其中*地區設定*是特定文化特性名稱。  
  
5.  開啟每個.resx 檔修改成適合特定語言和文化特性的字串值。 下列範例會顯示工具視窗的標題列的當地語系化的資源定義。  
  
     [Resources.en US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>併入專案中的當地語系化的資源  
 您必須修改 assemblyinfo.cs 檔案和專案檔，以將當地語系化的資源。  
  
1.  從**屬性**節點**方案總管 中**，在編輯器中開啟 assemblyinfo.cs 或 assemblyinfo.vb。  
  
2.  新增下列項目。  
  
    ```c#  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     英文 （美國） 設定為預設語言。  
  
3.  卸載專案。  
  
4.  在編輯器中開啟專案檔案。  
  
5.  找出`ItemGroup`包含項目`EmbeddedResource`項目。  
  
6.  在`EmbeddedResource`VSPackage.en US.resx，會呼叫的項目取代`ManifestResourceName`具有項目`LogicalName`元素，設定為`VSPackage.en-US.Resources`、，如下所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  對於每個當地語系化的語言，複製`EmbeddedResource`VsPackage.en 美式和集合的項目**包含**屬性和**LogicalName**複製的目標地區設定，如下列範例所示的項目。  
  
8.  每個當地語系化`VSCTCompile`項目，加入`ResourceName`指向項目的`Menus.ctmenu`，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. 儲存專案檔，並重新載入專案。  
  
10. 建置專案。  
  
     這會建立主要組件，並針對每種語言的資源組件。 當地語系化的部署程序的資訊，請參閱[當地語系化 VSIX 套件](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)   
 [MenuCommand 對比OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [全球化和當地語系化](http://msdn.microsoft.com/Library/9a59696b-d89b-45bd-946d-c75da4732d02)
