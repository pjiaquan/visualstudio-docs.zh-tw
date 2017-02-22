---
title: "建立可重複使用的按鈕群組 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "在 Vspackage 中建立的按鈕群組"
  - "VSPackages，建立可重複使用的按鈕群組"
  - "按鈕，建立可重複使用的群組"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
caps.handback.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
---
# 建立可重複使用的按鈕群組
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

命令群組是一律一起出現的功能表或工具列的命令集合。 可以重複使用任何命令群組，藉由指派至不同的父功能表.vsct 檔的 CommandPlacements 區段中。  
  
 命令群組通常包含按鈕，但也可以包含其他功能表或下拉式方塊。  
  
### 若要建立一組可重複使用按鈕  
  
1.  建立 VSIX 專案，名為 `ReusableButtons`。 如需詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  專案開啟時，加入名為的自訂命令項目範本 **ReusableCommand**。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂命令**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **ReusableCommand.cs**。  
  
3.  在.vsct 檔案中，移至 \[符號\] 區段，並尋找 GuidSymbol 項目，其中包含群組和專案的命令。 它應該命名為 guidReusableCommandPackageCmdSet。  
  
4.  新增 IDSymbol 為每個按鈕，您將新增至群組，如下列範例所示。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     根據預設，命令項目範本會建立一個名為群組 **MyGroup** 和按鈕所提供，以及每個 IDSymbol 項目名稱。  
  
5.  在 \[群組\] 區段中，建立具有相同的 GUID 和 ID 屬性的 Symbols 區段中指定的群組項目。 您也可以使用現有的群組，或使用所提供的命令範本，如下列範例所示的項目。 此群組會出現在 **工具** 功能表  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### 若要建立一組按鈕，以供重複使用  
  
1.  您可以將命令或功能表群組中使用群組與父系定義中的命令或功能表上，或使用 CommandPlacements 區段中將命令或功能表放在群組中。  
  
     \[按鈕\] 區段中定義您的群組，做為其父系，按鈕或使用按鈕所提供的 \[套件\] 範本，如下列範例所示。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  如果按鈕必須出現在多個群組，請為其建立項目 CommandPlacements 節必須後面命令 \> 一節。 設定以符合您要放置的按鈕 CommandPlacement 項目的 GUID 和 ID 屬性，然後設定的 GUID 和其父項目 ID 的目標群組，如下列範例所示。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  \[優先順序\] 欄位的值決定命令的位置，在新的命令群組中。 項目會覆寫設定項目定義 CommandPlacement 中設定的優先權。 具有較高的優先順序值的命令之前，會顯示具有較低的優先順序值的命令。 允許重複的優先順序值，但是無法保證有相同的優先順序值的命令的相對位置，因為順序 **devenv \/setup** 命令會建立最終介面從登錄可能不一致。  
  
### 將一組可重複使用按鈕功能表上  
  
1.  建立中的項目 `CommandPlacements` 一節。 設定的 GUID 和 ID `CommandPlacement` 項目與您的群組，並將父 GUID 和 ID 設定為與目標位置。  
  
     CommandPlacements 區段應該有後方命令 \> 一節:  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     命令群組可以包含多個功能表上。 在父功能表可以一次建立時，所提供的其中一個 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(如所述 ShellCmdDef.vsct 或 SharedCmdDef.vsct\)，或在另一個的 VSPackage 中定義的其中一個。 父圖層的數目沒有限制，只要在父功能表最後連至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或 VSPackage 會顯示快顯功能表。  
  
     下列範例會將群組放 **方案總管\] 中** 工具列中，右邊的 \[其他\] 按鈕。  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```