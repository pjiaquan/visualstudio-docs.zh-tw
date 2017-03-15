---
title: "使用 「 設定存放區 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設定存放區中，使用"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# 使用 「 設定存放區
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有兩種類型的設定存放區:  
  
-   組態設定是唯讀的 Visual Studio 和 VSPackage 設定。 Visual Studio 會將所有已知的.pkgdef 檔的設定，此存放區合併。  
  
-   使用者設定，也就是可寫入的設定，例如在頁面上看到的 **選項** 對話方塊、 屬性頁和某些其他對話方塊。 Visual Studio 擴充功能可能會使用這些本機存放裝置的少量資料。  
  
 本逐步解說示範如何讀取組態設定存放區中的資料。 請參閱 [寫入使用者設定存放區](../extensibility/writing-to-the-user-settings-store.md) 如何寫入使用者設定存放區的說明。  
  
## 建立範例專案  
 本節說明如何建立簡單的延伸模組專案示範的功能表命令。  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含擴充資產。 建立 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX 專案，名為 `SettingsStoreExtension`。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  現在加入名為的自訂命令項目範本 **SettingsStoreCommand**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **自訂命令**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **SettingsStoreCommand.cs**。 如需如何建立自訂命令的詳細資訊，請參閱 [建立擴充功能的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## 使用組態設定存放區  
 本節說明如何偵測並顯示組態設定。  
  
1.  在 SettingsStorageCommand.cs 檔案中，新增下列 using 陳述式:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  在 `MenuItemCallback`, 、 移除方法的主體，並新增下列程式碼行取得組態設定存放區:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> 是一個 managed 的 helper 類別，透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 服務。  
  
3.  現在請了解是否要安裝 Windows Phone 工具。 程式碼看起來應該像這樣:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  測試程式碼。 建置此專案並開始偵錯。  
  
5.  在實驗性的執行個體，在 **工具** \] 功能表上，按一下 \[ **叫用 SettingsStoreCommand**。  
  
     您應該會看到訊息指出 **Microsoft Windows Phone 開發人員工具:**  後面 **True** 或 **False**。  
  
 Visual Studio 會保留在系統登錄中設定存放區。  
  
#### 若要使用登錄編輯程式來確認組態設定  
  
1.  開啟 Regedit.exe。  
  
2.  瀏覽至 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\。  
  
    > [!NOTE]
    >  請確定您正在查看該索引鍵包含 \\14.0Exp\_Config\\ 和不 \\14.0\_Config\\。 當您執行的 Visual Studio 的實驗執行個體時，組態設定是在登錄區 「 14.0Exp\_Config 」。  
  
3.  展開 \\Installed Products\\ 節點。 如果在先前步驟中的訊息是 **Microsoft Windows Phone 開發人員工具安裝: True**, ，則 \\Installed Products\\ 應該包含 Microsoft Windows Phone 開發人員工具\] 節點。 如果訊息是 **Microsoft Windows Phone 開發人員工具安裝: False**, ，然後 \\Installed Products\\ 不應包含 Microsoft Windows Phone 開發人員工具\] 節點。