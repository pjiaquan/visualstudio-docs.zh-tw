---
title: "逐步解說：手動部署 ClickOnce 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 手動"
  - "ClickOnce 部署, SDK 工具"
  - "部署應用程式 [ClickOnce], 手動 ClickOnce 部署"
  - "Mage.exe, 手動 ClickOnce 部署"
  - "MageUI.exe, 手動 ClickOnce 部署"
  - "資料清單 [ClickOnce]"
  - "手動 ClickOnce 部署"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 逐步解說：手動部署 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您無法使用 Visual Studio 部署 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，或是需要使用進階部署功能 \(如信任的應用程式部署\)，就應該使用 Mage.exe 命令列工具來建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 資訊清單。  本逐步解說將說明如何使用命令列版本 \(Mage.exe\) 或圖形化版本 \(MageUI.exe\) 的「資訊清單產生和編輯工具」來建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署。  
  
## 必要條件  
 本逐步解說包含建置部署前必須先選擇的一些必要條件和選項。  
  
-   安裝 Mage.exe 和 MageUI.exe。  
  
     Mage.exe 和 MageUI.exe 是 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 的一部分。  您必須已經安裝 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]，或是有隨附於 Visual Studio 的 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 版本。  如需詳細資訊，請參閱 MSDN 上的 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044)。  
  
-   提供要部署的應用程式。  
  
     本逐步解說假設您手邊有準備要部署的 Windows 應用程式。  這個應用程式稱為 AppToDeploy。  
  
-   決定如何散發部署。  
  
     散發選項包括：Web、檔案共用或光碟片。  如需詳細資訊，請參閱 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)。  
  
-   判斷應用程式是否需要更高的信任層級。  
  
     如果應用程式需要完全信任 \(例如，使用者系統的完整存取權限\)，您可以使用 Mage.exe 的 `-TrustLevel` 選項來設定此項。  如果要為應用程式定義自訂權限集合，您可以從其他資訊清單複製網際網路或內部網路權限區段，加以修改以適應您的需要，並使用文字編輯器或 MageUI.exe 將之加入至應用程式資訊清單。  如需詳細資訊，請參閱 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
-   取得 Authenticode 憑證。  
  
     您應該以 Authenticode 憑證來簽署部署。  您可以使用 Visual Studio、MageUI.exe、MakeCert.exe 和 Pvk2Pfx.exe 工具產生測試憑證，或是從憑證授權單位 \(Certificate Authority，CA\) 取得憑證。  如果選擇使用受信任的應用程式部署，您就必須對所有的用戶端電腦執行憑證的一次安裝。  如需詳細資訊，請參閱 [受信任的應用程式部署概觀](../deployment/trusted-application-deployment-overview.md)。  
  
-   確定應用程式沒有內含 UAC 資訊的資訊清單。  
  
     您必須判斷應用程式是否包含具有使用者帳戶控制 \(User Account Control，UAC\) 資訊的資訊清單，例如 `<dependentAssembly>` 項目。  若要檢查資訊清單，可以使用 Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) 公用程式。  
  
     如果應用程式包含具有 UAC 詳細資料的資訊清單，您必須重新建置不含 UAC 資訊的應用程式。  如果是 Visual Studio 中的 C\# 專案，請開啟專案屬性並選取 \[應用程式\] 索引標籤。  在 \[**資訊清單**\] 下拉式清單中，選取 \[**建立無資訊清單應用程式**\]。  如果是 Visual Studio 中的 Visual Basic 專案，請開啟專案屬性、選取 \[應用程式\] 索引標籤，然後按一下 \[**檢視 UAC 設定**\]。  在開啟的資訊清單檔中，移除單一 `<asmv1:assembly>` 項目內的所有項目。  
  
-   判斷應用程式在用戶端電腦上所需的必要條件。  
  
     從 Visual Studio 部署的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式可以將必要條件安裝啟動載入器 \(setup.exe\) 隨附在部署中。  本逐步解說將建立兩份 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署需要的資訊清單。  您可以使用 [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md)來建立必要條件啟動載入器。  
  
### 若要以 Mage.exe 命令列工具部署應用程式  
  
1.  建立用來存放 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署檔案的目錄。  
  
2.  在剛才建立的部署目錄中，建立版本子目錄。  如果這是第一次部署應用程式，請將版本子目錄命名為 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能有別於應用程式的版本。  
  
3.  將所有的應用程式檔案複製到版本子目錄，包括可執行檔、組件、資源及資料檔。  若有必要，可以建立包含其他檔案的額外子目錄。  
  
4.  開啟 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 或 Visual Studio 命令提示字元，並移至版本子目錄。  
  
5.  呼叫 Mage.exe 以建立應用程式資訊清單。  下列陳述式會為編譯後要在 Intel x86 處理器上執行的程式碼建立應用程式資訊清單。  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  請務必在 `-FromDirectory` 選項後加上句號 \(.\)，表示指定目前的目錄。  如果沒有加上句號，就必須指定應用程式檔案的路徑。  
  
6.  以 Authenticode 憑證簽署應用程式資訊清單。  以憑證檔路徑取代 *mycert.pfx*。  以憑證檔密碼取代 *passwd*。  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  移至部署目錄的根目錄。  
  
8.  呼叫 Mage.exe 以產生部署資訊清單。  根據預設，Mage.exe 會將您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署標記為已安裝的應用程式，如此就能在線上和離線模式執行。  若要讓應用程式只能在使用者處於線上時執行，請使用 `-Install` 選項並將值設定為 `false`。  如果使用預設值，且使用者會從網站或檔案共用安裝您的應用程式，請確定 `-ProviderUrl` 選項的值是指向 Web 伺服器或共用上應用程式資訊清單的位置。  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. 以 Authenticode 憑證簽署部署資訊清單。  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. 將部署目錄中的所有檔案複製到部署目的地或媒體。  這可能是網站或 FTP 站台上的資料夾、檔案共用，或是 CD\-ROM。  
  
11. 提供使用者安裝應用程式所需的 URL、UNC 或實體媒體。  如果提供 URL 或 UNC，您就必須給予使用者部署資訊清單的完整路徑。  例如，如果將 AppToDeploy 部署至 http:\/\/webserver01\/ 上的 AppToDeploy 目錄，則完整的 URL 路徑就會是 http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application。  
  
### 若要以 MageUI.exe 圖形工具部署應用程式  
  
1.  建立用來存放 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署檔案的目錄。  
  
2.  在剛才建立的部署目錄中，建立版本子目錄。  如果這是第一次部署應用程式，請將版本子目錄命名為 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能有別於應用程式的版本。  
  
3.  將所有的應用程式檔案複製到版本子目錄，包括可執行檔、組件、資源及資料檔。  若有必要，可以建立包含其他檔案的額外子目錄。  
  
4.  啟動 MageUI.exe 圖形工具。  
  
    ```  
    MageUI.exe  
    ```  
  
5.  從功能表依序選取 \[**檔案**\]、\[**新增**\]、\[**應用程式資訊清單**\]，以建立新的應用程式資訊清單。  
  
6.  在預設的 \[**名稱**\] 索引標籤上，輸入此部署的名稱和版本號碼。  此外，還要指定應用程式的建置目標 \[**處理器**\]，例如 x86。  
  
7.  選取 \[**檔案**\] 索引標籤，然後按一下 \[**應用程式目錄**\] 文字方塊旁邊的省略符號 \(**...**\) 按鈕。  \[瀏覽資料夾\] 對話方塊隨即出現。  
  
8.  選取包含應用程式檔案的版本子目錄，然後按一下 \[**確定**\]。  
  
9. 如果您將會從 Internet Information Services \(IIS\) 進行部署，請選取 \[**填入時將 .deploy 副檔名加到沒有此副檔名的任何檔案**\] 核取方塊。  
  
10. 按一下 \[**填入**\] 按鈕，將所有的應用程式檔案加入到檔案清單中。  如果您的應用程式含有一個以上的可執行檔，請從 \[**檔案類型**\] 下拉式清單選取 \[**進入點**\]，將此部署的主要可執行檔標記為啟動應用程式   \(如果您的應用程式只含有一個可執行檔，MageUI.exe 將會為您標記該檔\)。  
  
11. 選取 \[**所需權限**\] 索引標籤，並選取應用程式判斷提示需要的信任層級。  預設值為 \[**FullTrust**\]，這個值適用於多數的應用程式。  
  
12. 從功能表中選取 \[**檔案**\]，然後選取 \[**另存新檔**\]。  \[簽署選項\] 對話方塊隨即出現，並提示您簽署應用程式資訊清單。  
  
13. 如果在檔案系統上有儲存為檔案的憑證，請使用 \[**用憑證檔簽署**\] 選項，並使用省略符號 \(**...**\) 按鈕從檔案系統選取憑證，  然後輸入憑證密碼。  
  
     \-或\-  
  
     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 \[**用儲存的憑證簽署**\] 選項，並從提供的清單中選取憑證。  
  
14. 按一下 \[**確定**\] 簽署應用程式資訊清單。  \[另存新檔\] 對話方塊隨即出現。  
  
15. 在 \[另存新檔\] 對話方塊中指定版本目錄，然後按一下 \[**儲存**\]。  
  
16. 從功能表依序選取 \[**檔案**\]、\[**新增**\] 和 \[**部署資訊清單**\]，建立部署資訊清單。  
  
17. 在 \[**名稱**\] 索引標籤上，指定此部署的名稱和版本號碼 \(在本範例中為 1.0.0.0\)。  此外，還要指定應用程式的建置目標 \[**處理器**\]，例如 x86。  
  
18. 選取 \[**描述**\] 索引標籤，並指定 \[**發行者**\] 和 \[**產品**\] 的值   \(\[**產品**\] 是將應用程式安裝在用戶端電腦以供離線使用時，在 Windows \[開始\] 功能表上顯示的應用程式名稱\)。  
  
19. 選取 \[**部署選項**\] 索引標籤，並在 \[**開始位置**\] 文字方塊中指定 Web 伺服器或共用上應用程式資訊清單的名稱。  例如，\\\\myServer\\myShare\\AppToDeploy.application。  
  
20. 如果您在前面的步驟中加入了 .deploy 副檔名，也請在這裡選取 \[**使用 .deploy 副檔名**\]。  
  
21. 選取 \[**更新選項**\] 索引標籤，並指定您想要多久更新此應用程式一次。  如果應用程式使用 <xref:System.Deployment.Application.UpdateCheckInfo> 來自我檢查更新，請清除 \[**此應用程式應檢查是否有更新**\] 核取方塊。  
  
22. 選取 \[**應用程式參考**\] 索引標籤，然後按一下 \[**選取資訊清單**\] 按鈕。  \[開啟舊檔\] 對話方塊隨即出現。  
  
23. 選取先前建立的應用程式資訊清單，然後按一下 \[**開啟**\]。  
  
24. 從功能表中選取 \[**檔案**\]，然後選取 \[**另存新檔**\]。  \[簽署選項\] 對話方塊隨即出現，並提示您簽署部署資訊清單。  
  
25. 如果在檔案系統上有儲存為檔案的憑證，請使用 \[**用憑證檔簽署**\] 選項，並使用省略符號 \(**...**\) 按鈕從檔案系統選取憑證，  然後輸入憑證密碼。  
  
     \-或\-  
  
     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 \[**用儲存的憑證簽署**\] 選項，並從提供的清單中選取憑證。  
  
26. 按一下 \[**確定**\] 簽署部署資訊清單。  \[另存新檔\] 對話方塊隨即出現。  
  
27. 在 \[**另存新檔**\] 對話方塊中，上移一層目錄至部署的根目錄，然後按一下 \[**儲存**\]。  
  
28. 將部署目錄中的所有檔案複製到部署目的地或媒體。  這可能是網站或 FTP 站台上的資料夾、檔案共用，或是 CD\-ROM。  
  
29. 提供使用者安裝應用程式所需的 URL、UNC 或實體媒體。  如果提供 URL 或 UNC，您就必須給予使用者部署資訊清單的完整路徑。  例如，如果將 AppToDeploy 部署至 http:\/\/webserver01\/ 上的 AppToDeploy 目錄，則完整的 URL 路徑就會是 http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application。  
  
## 後續步驟  
 需要部署應用程式的新版本時，請建立新目錄並依照新版本來命名 \(例如，1.0.0.1\)，然後將新的應用程式檔案複製到新目錄。  接下來，您必須遵循前述步驟建立和簽署新的應用程式資訊清單，並更新和簽署部署資訊清單。  在使用 Mage.exe 搭配 `-New` 和 `–Update` 呼叫中指定同樣新的版本時要謹慎，因為 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 只會更新較新的版本，而版本的新舊是依最左邊整數為最高位數字的規則來判斷。  如果您使用的是 MageUI.exe，只要開啟部署資訊清單、選取 \[**應用程式參考**\] 索引標籤、按一下 \[**選取資訊清單**\] 按鈕，再選取更新的應用程式資訊清單，即可更新部署資訊清單。  
  
## 請參閱  
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 部署資訊清單](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)