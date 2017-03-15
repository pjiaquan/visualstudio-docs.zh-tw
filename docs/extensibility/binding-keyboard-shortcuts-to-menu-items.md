---
title: "功能表項目繫結的鍵盤快速鍵 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
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
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>功能表項目繫結的鍵盤快速鍵
要繫結的自訂功能表命令鍵盤快速鍵，只要加入一個項目.vsct 檔封裝。 本主題說明如何將鍵盤快速鍵對應至自訂按鈕、 功能表項目或工具列命令，以及如何套用的預設編輯器中的鍵盤對應或限制成自訂編輯器。  
  
 若要將鍵盤快速鍵指派給現有的 Visual Studio 功能表項目，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。  
  
## <a name="choosing-a-key-combination"></a>選擇按鍵組合  
 許多的鍵盤快速鍵已可用於 Visual Studio。 您不應該指派多個命令相同的快顯，因為重複的繫結很難偵測得到，而且也可能會造成無法預期的結果。 因此，最好確認捷徑的可用性，再將它指派。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>若要確認可用性的鍵盤快速鍵  
  
1.  在**工具 / 選項 / 環境**視窗中，選取**鍵盤**。  
  
2.  請確定**新的快速鍵用於**設為**Global**。  
  
3.  在**按快速鍵**方塊中，輸入您想要使用的鍵盤快速鍵。  
  
     如果已經在 Visual Studio 中，使用捷徑**目前所使用的捷徑**方塊會顯示快顯目前呼叫的命令。  
  
4.  嘗試不同的組合索引鍵，直到找到未對應。  
  
    > [!NOTE]
    >  使用 alt 鍵的鍵盤快速鍵可能開啟功能表，並不會直接執行命令。 因此，**目前所使用的捷徑**方塊可能是空白，當您輸入包含 ALT 捷徑。 您可以確認捷徑不會透過關閉開啟的功能表**選項**對話方塊，然後按下按鍵。  
  
 下列程序假設您有現有的 VSPackage 的功能表命令。 如果您需要這麼做可協助，看看[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>若要指派給某命令的鍵盤快速鍵  
  
1.  開啟您的封裝.vsct 檔。  
  
2.  建立空白`<KeyBindings>`區段之後`<Commands>`如果尚不存在。  
  
    > [!WARNING]
    >  如需索引鍵繫結的詳細資訊，請參閱[Keybinding](../extensibility/keybinding-element.md)。  
  
     在`<KeyBindings>`區段中，建立`<KeyBinding>`項目。  
  
     設定`guid`和`id`您想要叫用命令的屬性。  
  
     設定`mod1`屬性設定為**控制項**， **Alt**，或**Shift**。  
  
     按鍵組合區段看起來應該像這樣︰  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 如果鍵盤快速鍵需要兩個以上的索引鍵，將`mod2`和`key2`屬性。  
  
 在大部分情況下， **Shift**不應該使用第二個修飾詞不因為它已按下會導致大部分英數字元的按鍵輸入大寫的字母或符號。  
  
 虛擬按鍵碼可讓您存取並沒有字元，例如，函式的索引鍵與其相關聯的特殊按鍵而**退格鍵**索引鍵。 如需詳細資訊，請參閱[虛擬按鍵碼](http://go.microsoft.com/fwlink/?LinkID=105932)。  
  
 若要讓命令在 Visual Studio 編輯器，設定`editor`屬性設定為`guidVSStd97`。  
  
 若要將此命令只適用於自訂編輯器，將`editor`屬性名稱的自訂編輯器所產生的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]套件 範本建立時的 VSPackage，包括自訂編輯器。 若要尋找的名稱值，請查看`<Symbols>`區段`<GuidSymbol>`節點的`name`屬性以 「`editorfactory`。 」這是自訂編輯器的名稱。  
  
## <a name="example"></a>範例  
 此範例中繫結至名為命令的鍵盤快速鍵 CTRL + ALT + C`cmdidMyCommand`中名為套件`MyPackage`。  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>範例  
 此範例中繫結至名為命令的鍵盤快速鍵 CTL + B`cmdidBold`在專案中名為`TestEditor`。 此命令為僅適用於自訂編輯器和不在其他編輯器。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../extensibility/extending-menus-and-commands.md)
