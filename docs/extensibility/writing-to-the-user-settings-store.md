---
title: "使用者設定存放區寫入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
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
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區
使用者設定為可寫入的設定，像是在**工具 / 選項**對話方塊中，屬性 視窗中，並確定其他對話方塊。 Visual Studio 擴充功能可以使用這些儲存小量的資料。 本逐步解說示範如何加入 [記事本] Visual Studio 外部工具為讀取和寫入使用者設定存放區。  
  
### <a name="backing-up-your-user-settings"></a>備份您的使用者設定  
  
1.  您必須能夠重設的外部工具設定，以便您可以偵錯，並重複此程序。 若要這樣做，您必須儲存原始設定，因此您可以視需要予以還原。  
  
2.  開啟 Regedit.exe。  
  
3.  瀏覽至 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External 工具\\。  
  
    > [!NOTE]
    >  請確定您正在查看該索引鍵包含 \14.0Exp\ 和不 \14.0\\。 當您執行的 Visual Studio 的實驗執行個體時，您的使用者設定是在登錄區 「&14;.0Exp 」。  
  
4.  \External Tools\ 子機碼，以滑鼠右鍵按一下，然後按一下 **匯出**。 請確定**選取分支**已選取。  
  
5.  儲存產生的外部 Tools.reg 檔案。  
  
6.  稍後，當您想要重設為外部工具設定，選取 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External 工具的登錄機碼，然後按一下 **刪除**快顯功能表上。  
  
7.  當**確認機碼刪除**對話方塊出現時，按一下**是**。  
  
8.  以滑鼠右鍵按一下您稍早儲存的外部 Tools.reg 檔案中，按一下**開啟**，然後按一下 **登錄編輯程式**。  
  
## <a name="writing-to-the-user-settings-store"></a>寫入使用者設定存放區  
  
1.  建立名為 UserSettingsStoreExtension VSIX 專案，並新增名為 UserSettingsStoreCommand 自訂命令。 如需如何建立自訂命令的詳細資訊，請參閱[建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  在 UserSettingsStoreCommand.cs，新增下列 using 陳述式︰  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  在 MenuItemCallback，刪除方法的主體，並取得的使用者設定存放區，，如下所示︰  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  現在找出 記事本 是否已設為 外部工具。 您必須逐一查看所有外部的工具，來判斷是否 ToolCmd 設定 「 記事本 」，如下所示︰  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  如果尚未設定成外部工具 [記事本]，請以下列方式設定︰  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  測試程式碼。 請記住，它會將新增 「 記事本 」 外部工具，因此您必須回復登錄第二次執行之前。  
  
7.  建置程式碼，並開始偵錯。  
  
8.  在**工具**] 功能表上，按一下 [**叫用 UserSettingsStoreCommand**。 這會將 [記事本] 來新增**工具**功能表。  
  
9. 現在您應該會看到 記事本 的工具 / 選項 功能表，並按一下**記事本**應該啟動記事本的執行個體。
