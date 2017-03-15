---
title: "逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式 | Microsoft Docs"
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
  - "品牌"
  - "ClickOnce 應用程式, 由其他人部署"
  - "ClickOnce 部署, 手動"
  - "ClickOnce 部署, SDK 工具"
  - "客戶部署"
  - "資料清單 [ClickOnce]"
  - "手動 ClickOnce 部署"
  - "多個 ClickOnce 部署和品牌"
  - "保留品牌資訊"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 逐步解說：手動部署不需要重新簽署而且會保留商標資訊的 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，然後將它交給客戶發行及部署時，客戶以往都會需要更新部署資訊清單並重新簽署。雖然這種方法仍是大部分情況下偏好使用的方法，不過 .NET Framework 3.5 能讓您建立可由客戶部署的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署，而不需產生新的部署資訊清單。  如需詳細資訊，請參閱 [針對測試和實際執行伺服器部署 ClickOnce 應用程式但不重新簽章](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)。  
  
 當您建立 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，然後將它交給客戶發行及部署時，應用程式可使用客戶的品牌或是保留您的品牌。  例如，如果應用程式是單一專屬應用程式，您可能想要保留您的品牌。  如果應用程式可針對每位客戶高度自訂，則您可能想要使用客戶的品牌。  當您將應用程式交給某個組織部署時，.NET Framework 3.5 可讓您保留品牌、發行者資訊及安全性簽章。  如需詳細資訊，請參閱 [建立 ClickOnce 應用程式供其他人部署](../deployment/creating-clickonce-applications-for-others-to-deploy.md)。  
  
> [!NOTE]
>  在本逐步解說中，您將使用命令列工具 Mage.exe 或是圖形工具 MageUI.exe 手動建立部署。  如需手動部署的詳細資訊，請參閱[逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## 必要條件  
 若要執行這個逐步解說中的步驟，您需要以下各項：  
  
-   您準備要部署的 Windows Form 應用程式。  這個應用程式將稱為 WindowsFormsApp1。  
  
-   Visual Studio 或 Windows SDK。  
  
### 使用 Mage.exe 部署包含多個部署和品牌支援的 ClickOnce 應用程式  
  
1.  開啟 Visual Studio 命令提示字元或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示字元，並且切換到將儲存 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檔案的目錄。  
  
2.  建立目錄，並依照部署的目前版本命名。  如果這是第一次部署此應用程式，就可能會選擇 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能會有別於應用程式檔案的版本。  
  
3.  建立名為 bin 的子目錄，並將所有的應用程式檔案複製到此處，其中包括可執行檔、組件、資源及資料檔。  
  
4.  呼叫 Mage.exe 以產生應用程式資訊清單。  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  使用您的數位憑證簽署應用程式資訊清單。  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  呼叫 Mage.exe 以產生部署資訊清單。  根據預設，Mage.exe 會將您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署標記為已安裝的應用程式，如此就能在線上和離線模式執行。  若要使應用程式只能在使用者位於線上時執行，請使用具有 `f` 值的 `-i` 引數。  由於這個應用程式將利用多重部署功能，因此呼叫 Mage.exe 時請勿搭配 `-providerUrl` 引數   \(在 .NET Framework 3.5 之前的版本中，若離線應用程式未包含 `-providerUrl`，將導致錯誤發生\)。  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  請勿簽署部署資訊清單。  
  
8.  提供所有檔案給將在其網路上部署應用程式的客戶。  
  
9. 至此，客戶必須使用其自動產生的憑證簽署部署資訊清單。  例如，如果客戶為名為 Adventure Works 的公司工作，則可使用 MakeCert.exe 工具產生自動簽署的憑證。  接著，使用 Pvk2pfx.exe 工具將 MakeCert.exe 建立的檔案組合成可傳遞至 Mage.exe 的 PFX 檔案。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. 接著客戶將使用這個憑證簽署部署資訊清單。  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. 客戶將應用程式部署至其使用者。  
  
### 使用 MageUI.exe 部署包含多個部署和品牌支援的 ClickOnce 應用程式  
  
1.  開啟 Visual Studio 命令提示字元或 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 命令提示字元，並且巡覽至將儲存 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 檔案的目錄。  
  
2.  建立名為 bin 的子目錄，並將所有的應用程式檔案複製到此處，其中包括可執行檔、組件、資源及資料檔。  
  
3.  建立子目錄，並依照部署的目前版本命名。  如果這是第一次部署此應用程式，就可能會選擇 1.0.0.0。  
  
    > [!NOTE]
    >  部署的版本可能會有別於應用程式檔案的版本。  
  
4.  將 \\bin 目錄移至您在步驟 2 中建立的目錄。  
  
5.  啟動圖形工具 MageUI.exe。  
  
    ```  
    MageUI.exe  
    ```  
  
6.  從功能表依序選取 \[**檔案**\]、\[**新增**\]、\[**應用程式資訊清單**\]，以建立新的應用程式資訊清單。  
  
7.  在預設的 \[**名稱**\] 索引標籤上，輸入此部署的名稱和版本號碼。  同時提供 \[**發行者**\] 的值，該值將在部署時，用來做為 \[開始\] 功能表中應用程式捷徑連結的資料夾名稱。  
  
8.  選取 \[**應用程式選項**\] 索引標籤，然後按一下 \[**使用應用程式資訊清單供信任資訊使用**\]。  如此將針對這個 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式使用協力廠商品牌。  
  
9. 選取 \[**檔案**\] 索引標籤，並按一下 \[應用程式目錄\] 文字方塊旁的 \[**瀏覽**\] 按鈕。  
  
10. 選取您在步驟 2 中建立，含有應用程式檔案的目錄，並在 \[資料夾選取\] 對話方塊中，按一下 \[**確定**\]。  
  
11. 按一下 \[**填入**\] 按鈕，將所有的應用程式檔案加入到檔案清單中。  如果您的應用程式含有一個以上的可執行檔，請從 \[**檔案類型**\] 下拉式清單選取 \[**進入點**\]，將此部署的主要可執行檔標記為啟動應用程式   \(如果您的應用程式只含有一個可執行檔，MageUI.exe 將會為您標記該檔\)。  
  
12. 選取 \[**必要的使用權限**\] 索引標籤，並選取需要應用程式判斷提示的信任層級。  預設值為 \[**完全信任**\]，將會適用於多數的應用程式。  
  
13. 從功能表依序選取 \[**檔案**\] 及 \[**儲存**\]，並儲存應用程式資訊清單。  在儲存時，將會收到對應用程式資訊清單簽章的提示。  
  
14. 如果在檔案系統上擁有儲存為檔案的憑證，請使用 \[**簽章為憑證檔**\] 選項，並使用省略符號 \(**...**\) 按鈕從檔案系統選取憑證。  
  
     \-或\-  
  
     如果您的憑證保留在可從電腦存取的憑證存放區中，請選取 \[**以預存的憑證選項簽章**\]，並從提供的清單中選取憑證。  
  
15. 從功能表依序選取 \[**檔案**\]、\[**新增**\] 及 \[**部署資訊清單**\]，以建立您的部署資訊清單，然後在 \[**名稱**\] 索引標籤上，提供名稱和版本號碼 \(在此範例中為 1.0.0.0\)。  
  
16. 切換至 \[**更新**\] 索引標籤，並指定您要更新此應用程式的頻率。  如果應用程式使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署 API 來自我檢查更新，請清除標記為 \[**此應用程式應該檢查更新檔**\] 的核取方塊。  
  
17. 切換至 \[**應用程式參考**\] 索引標籤。  按一下 \[**選取資訊清單**\] 按鈕，並選取您在先前步驟中建立的應用程式資訊清單，即可在此索引標籤上預先填入所有的值。  
  
18. 選擇 \[**儲存**\]，並將部署資訊清單儲存至磁碟。  在儲存時，將會收到對應用程式資訊清單簽章的提示。  按一下 \[**取消**\] 儲存資訊清單，但不簽署。  
  
19. 提供所有應用程式檔案給客戶。  
  
20. 至此，客戶必須使用其自動產生的憑證簽署部署資訊清單。  例如，如果客戶為名為 Adventure Works 的公司工作，則可使用 MakeCert.exe 工具產生自動簽署的憑證。  接著，使用 Pvk2pfx.exe 工具將 MakeCert.exe 建立的檔案組合成可傳遞至 MageUI.exe 的 PFX 檔案。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 有了產生的憑證後，客戶現在將開啟 MageUI.exe 中的部署資訊清單再將它儲存，藉此簽署部署資訊清單。  簽署對話方塊出現時，客戶將選取 \[**簽署為憑證檔**\] 選項，然後選擇儲存在磁碟上的 PFX 檔案。  
  
22. 客戶將應用程式部署至其使用者。  
  
## 後續步驟  
  
## 請參閱  
 [Mage.exe \(資訊清單產生和編輯工具\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)