---
title: "如何：發行已啟用視覺化樣式的 WPF 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# 如何：發行已啟用視覺化樣式的 WPF 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

視覺化樣式讓通用控制項的外觀可根據使用者選擇的佈景主題變更。  根據預設，視覺化樣式不為 Windows Presentation Foundation \(WPF\) 應用程式啟用，因此，您必須手動啟用它們。  不過，啟用 WPF 應用程式的視覺化樣式來發行方案時會產生錯誤。  本主題說明如何解決這個錯誤和發行已啟用視覺化樣式的 WPF 應用程式之流程。  如需視覺化樣式的詳細資訊，請參閱 [Visual Styles Overview](http://msdn.microsoft.com/zh-tw/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)。  如需錯誤訊息的詳細資訊，請參閱 [疑難排解 ClickOnce 部署的特定錯誤](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)。  
  
 若要解決這個錯誤和發行方案，您必須執行下列工作：  
  
-   [發行沒有啟用視覺化樣式的方案。](#BKMK_publishsolwovs)。  
  
-   [建立資訊清單檔案](#BKMK_CreateManifest)  
  
-   [內嵌資訊清單檔至發行方案的可執行檔](#BKMK_embedmanifest)  
  
-   [簽署應用程式和部署資訊清單](#BKMK_signappdeplyman)  
  
 然後，您可以將發行的檔案移至您希望使用者安裝應用程式的位置。  
  
##  <a name="BKMK_publishsolwovs"></a> 發行沒有啟用視覺化樣式的方案。  
  
1.  確定您的專案未啟用視覺化樣式。  首先，請檢查下列專案資訊清單檔中的 XML。  如果 XML 存在，請將 XML 標記註解。  
  
     根據預設，視覺化樣式為不啟用狀態。  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     下列程序示範如何開啟與您的專案相關聯的資訊清單檔。  
  
    ###### 開啟 Visual Basic 專案中的資訊清單檔案  
  
    1.  在選單列中，選擇 \[**專案**\]，\[*ProjectName***Properties**\]，其中 \[*ProjectName*\] 是您的 WPF 專案名稱。  
  
         WPF 專案的屬性頁隨即出現。  
  
    2.  在 \[**應用程式**\] 索引標籤上，選取 \[**檢視視窗設定**\]。  
  
         app.manifest 檔案隨即在 **程式碼編輯器** 中開啟。  
  
    ###### 開啟 C\# 專案的資訊清單檔案  
  
    1.  在選單列中，選擇 \[**專案**\]，\[*ProjectName***Properties**\]，其中 \[*ProjectName*\] 是您的 WPF 專案名稱。  
  
         WPF 專案的屬性頁隨即出現。  
  
    2.  在 \[**應用程式**\] 索引標籤，請記下資訊清單欄位出現的名稱。  這是與專案關聯的資訊清單名稱。  
  
        > [!NOTE]
        >  若 \[**內嵌具有預設值的資訊清單檔**\] 或 \[**建立沒有資訊清單檔的應用程式**\] 出現在資訊清單欄位，則視覺化樣式未啟用。  如果資訊清單檔的名稱出現在資訊清單欄位，請執行這個程序中的下一個步驟。  
  
    3.  在 \[**方案總管**\] 中選取 \[**顯示所有檔案**\]。  
  
         這個按鈕顯示所有專案項目，包括已排除的以及通常會隱藏的。  資訊清單檔案會顯示為專案項目。  
  
2.  建置並發行方案。  如需如何發行方案的詳細資訊，請參閱 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)。  
  
##  <a name="BKMK_CreateManifest"></a> 建立資訊清單檔案  
  
1.  將下列 XML 貼到 \[記事本\] 檔案上。  
  
     這個 XML 描述該組件支援視覺化樣式的控制項。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  在 \[記事本\] 中按一下 \[**檔案**\]，然後按一下 \[**另存新檔**\]。  
  
3.  在 \[**另存新檔**\] 對話方塊的 \[**存檔類型**\] 下拉式清單中，選取 \[**所有檔案**\]。  
  
4.  在 \[**檔案名稱**\] 方塊中，為檔案命名並附加 .manifest 至檔案名稱的結尾。  例如：themes.manifest。  
  
5.  選擇 \[**瀏覽資料夾**\] 按鈕來選取任何資料夾，然後按一下 \[**儲存**\]。  
  
    > [!NOTE]
    >  其餘程序假設此檔案名稱是 themes.manifest，並將檔案儲存至電腦的 C:\\temp 目錄。  
  
##  <a name="BKMK_embedmanifest"></a> 內嵌資訊清單檔至發行方案的可執行檔  
  
1.  開啟 \[**Visual Studio 命令提示字元**\]。  
  
     如需如何使用 \[**Visual Studio 命令提示字元**\] 的詳細資訊，請參閱 [命令提示字元](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)。  
  
    > [!NOTE]
    >  其餘步驟假設您方案中有下列設定：  
    >   
    >  -   方案的名稱是 MyWPFProject。  
    > -   所在目錄為 `%UserProfile%\Documents\Visual Studio 2010\Projects\`。  
    >   
    >      方案發行到下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`。  
    > -   發行的應用程式檔案的最新版本位於下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  您不需要使用上述的名稱或目錄位置。  上述的名稱和位置只用來說明發行方案所需的步驟。  
  
2.  在命令提示字元，請變更路徑為含有已發行的應用程式檔案的最新版本之目錄。  以下範例示範此步驟。  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  在命令提示字元中執行下列命令，以內嵌資訊清單檔至應用程式的可執行檔。  
  
    ```  
    mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> 簽署應用程式和部署資訊清單  
  
1.  在命令提示字元中，執行下列命令會移除當前目錄的可執行檔中的 `.deploy` 副檔名。  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  這個範例假設只有一個檔案具有 `.deploy` 副檔名。  請確定您已將這個目錄中所有的 `.deploy` 副檔名重新命名。  
  
2.  在命令提示字元中，執行下列命令來簽署應用程式資訊清單。  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  這個範例假設您使用專案的 `.pfx` 檔案來簽署資訊清單。  若您並未要簽署資訊清單，您可以省略此範例中使用的 `–cf` 參數。  如果您簽署需要密碼憑證的資訊清單，請指定 `–password` 選項 \(`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\)。  
  
3.  在命令提示字元中，執行下列命令加入 `.deploy` 副檔名至您在先前步驟中重新命名的檔案。  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  這個範例假設只有一個檔案具有 `.deploy` 副檔名。  請確定您已為此目錄原本擁有 `.deploy` 附檔名的檔案重新命名。  
  
4.  在命令提示字元中，執行下列命令來簽署部署資訊清單。  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  這個範例假設您使用專案的 `.pfx` 檔案來簽署資訊清單。  若您並未要簽署資訊清單，您可以省略此範例中使用的 `–cf` 參數。  如果您簽署需要密碼憑證的資訊清單，請指定 `–password` 選項 \(如以下範例：`For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password`\)。  
  
 在您執行這些步驟之後，您可以將發行的檔案移至您希望使用者安裝應用程式的位置。  如果您打算經常更新方案，您可以將這些命令建立成指令碼檔案，並在每次發行新版本時執行這個指令碼檔案。  
  
## 請參閱  
 [疑難排解 ClickOnce 部署的特定錯誤](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visual Styles Overview](http://msdn.microsoft.com/zh-tw/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Enabling Visual Styles](VS|Controls|~\controls\userex\cookbook.htm)   
 [命令提示字元](../Topic/Developer%20Command%20Prompt%20for%20Visual%20Studio.md)