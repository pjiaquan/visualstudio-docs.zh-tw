---
title: "移轉舊版語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "語言服務移轉"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 移轉舊版語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以移轉至較新版的 Visual Studio 的舊版語言服務更新專案，並將 source.extension.vsixmanifest 檔案加入至專案。 語言服務本身將會繼續函式和之前一樣，因為 Visual Studio 編輯器會調整它。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱 [編輯器和語言服務擴充功能](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 移轉至更新版本的 Visual Studio 2008 語言服務方案  
 下列步驟示範如何調整名為 RegExLanguageService Visual Studio 2008 範例。 您可以尋找在 Visual Studio 2008 SDK 安裝中，此範例在 *Visual Studio SDK 安裝路徑*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ 資料夾。  
  
> [!IMPORTANT]
>  如果您的語言服務未定義的色彩，您必須明確設定 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> 至 `true` VSPackage 上︰  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### 若要移轉至更新版本的 Visual Studio 2008 語言服務  
  
1.  安裝新版本的 Visual Studio 和 Visual Studio SDK。 如需如何安裝 SDK 的詳細資訊，請參閱 [安裝 Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  編輯 RegExLangServ.csproj 檔案 （不含 Visual Studio 中載入。  
  
     在 `Import` 參照 Microsoft.VsSDK.targets 檔案中，節點的值取代成下列文字。  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  儲存檔案，然後關閉它。  
  
4.  開啟 RegExLangServ.sln 方案。  
  
5.  **單向升級** \] 視窗隨即出現。 按一下 \[確定\]。  
  
6.  更新專案屬性。 開啟 **專案屬性** \] 視窗中的選取專案節點中的 **方案總管\] 中**, 、 按一下滑鼠右鍵，然後選取 **屬性**。  
  
    -   在 **應用程式** 索引標籤上，變更 **目標 framework** 至 **4.6.1 在**。  
  
    -   在 **偵錯** 索引標籤的 **啟動外部程式** 方塊中，輸入 **\< Visual Studio 安裝路徑 \> \\Common7\\IDE\\devenv.exe。**。  
  
         在 **命令列引數** 方塊中，輸入 \/**rootsuffix Exp**。  
  
7.  更新下列參考︰  
  
    -   移除的參考，Microsoft.VisualStudio.Shell.9.0.dll，然後將參考加入 Microsoft.VisualStudio.Shell.14.0.dll 和 Microsoft.VisualStudio.Shell.Immutable.11.0.dll。  
  
    -   移除的參考，Microsoft.VisualStudio.Package.LanguageService.9.0.dll，然後加入 Microsoft.VisualStudio.Package.LanguageService.14.0.dll 的參考。  
  
    -   加入 Microsoft.VisualStudio.Shell.Interop.10.0.dll 的參考。  
  
8.  開啟 VsPkg.cs 檔案，然後將值變更 `DefaultRegistryRoot` 屬性  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. 原始範例不會註冊其語言服務，因此您必須將下列屬性加入至 VsPkg.cs。  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. 您必須新增 source.extension.vsixmanifest 檔案。  
  
    -   從現有的延伸模組的這個檔案複製到您的專案目錄中。 \(一個方法可取得這個檔案是建立 VSIX 專案 \(在 **檔案**, ，按一下 \[ **新增**, ，然後按一下 \[ **專案**。 在 Visual Basic 或 C\# 按一下 **擴充性**, ，然後選取 **VSIX 專案**。\)  
  
    -   將檔案加入至您的專案。  
  
    -   在檔案的 **屬性**, ，請將 **建置動作** 至 **無**。  
  
    -   開啟檔案 **VSIX 資訊清單編輯器**。  
  
    -   變更下列欄位︰  
  
    -   **識別碼**: RegExLangServ  
  
    -   **產品名稱**: RegExLangServ  
  
    -   **描述**︰ 規則運算式語言服務。  
  
    -   下 **資產**, ，按一下 **新增**, ，選取 **類型** 至 **Microsoft.VisualStudio.VsPackage**, ，請將 **來源** 至 **目前方案中的專案**, ，然後設定 **專案** 來 **RegExLangServ**。  
  
    -   儲存並關閉檔案。  
  
11. 建置方案。 建置的檔案會部署到 **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**。  
  
12. 開始偵錯。 開啟 Visual Studio 的第二個執行個體。  
  
## 請參閱  
 [舊版的語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)