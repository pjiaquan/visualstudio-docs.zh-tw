---
title: "MSI 和 VSIX 部署 DSL 的 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL 的 MSI 和 VSIX 部署
您可以在自己的電腦或其他電腦上安裝定義域專屬語言。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已經必須安裝在目標電腦上。  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>VSIX 和 MSI 部署之間選擇  
 有兩種部署網域特定語言︰  
  
|方法|優點|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能)|非常容易部署︰ 複製並執行**.vsix** DslPackage 專案檔。<br /><br /> 如需詳細資訊，請參閱[安裝和解除安裝 DSL 使用 VSX](#Installing)。|  
|MSI （安裝程式檔案）|-允許使用者開啟[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]按兩下 DSL 檔案。<br />-建立與目標電腦中的 DSL 檔案類型關聯圖示。<br />-將與 DSL 檔案類型關聯的 XSD （XML 結構描述）。 這可避免警告時載入此檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。<br /><br /> 您必須將安裝專案加入方案以建立 MSI。<br /><br /> 如需詳細資訊，請參閱[使用 MSI 檔案部署 DSL](#msi)。|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>安裝和使用 VSX 解除安裝 DSL  
 這個方法所安裝 DSL 時，使用者便可開啟 DSL 檔案內[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，但無法從 Windows 檔案總管中開啟檔案。  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>若要使用 VSX 安裝 DSL  
  
1.  在您的電腦，找出**.vsix** DSL 封裝專案所建置的檔案。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下**DslPackage**專案，然後再按一下**在 Windows 檔案總管 中開啟資料夾**。  
  
    2.  Locate the file **bin\\\*\\***YourProject***.DslPackage.vsix**  
  
2.  複製**.vsix**檔案到您要安裝 DSL 的目標電腦。 這可以是您自己的電腦或另一部電腦。  
  
    -   目標電腦必須有一個版本的[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]在執行階段支援的 Dsl。 如需詳細資訊，請參閱[視覺化 i 模型 sdk 支援 Visual Studio 版本](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。  
  
    -   目標電腦必須有一個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中所指定**DslPackage\source.extensions.manifest**。  
  
3.  目標電腦上，按兩下**.vsix**檔案。  
  
     [Visual Studio 擴充功能安裝程式] 會隨即開啟並安裝擴充功能。  
  
4.  啟動或重新啟動 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  
  
5.  若要測試 DSL，請使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]來建立新的檔案定義 DSL 的副檔名。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>若要解除安裝使用 VSX 所安裝的 DSL  
  
1.  在**工具**] 功能表上，按一下 [**擴充管理員**。  
  
2.  展開 [已安裝的擴充功能] 。  
  
3.  選取擴充功能，在其中定義 DSL，然後按一下 **解除安裝**。  
  
 在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>部署 MSI 中的 DSL  
 藉由定義您的 dsl 的 MSI (Windows Installer) 檔案，您可以允許使用者從 Windows 檔案總管開啟 DSL 檔案。 您也可以與您的檔案名稱副檔名關聯的圖示和簡短描述。 此外，MSI 可以安裝可以用來驗證 DSL 檔 XSD。 如果您想，您可以新增到將會同時安裝 MSI 的其他元件。  
  
 如需有關 MSI 檔案和其他部署選項的詳細資訊，請參閱[部署應用程式、 服務和元件](../deployment/deploying-applications-services-and-components.md)。  
  
 若要建置 MSI，您加入安裝專案中的加入您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案。 建立安裝專案的最簡單的方法是使用 CreateMsiSetupProject.tt 範本，您可以從下載[VMSDK 網站](http://go.microsoft.com/fwlink/?LinkID=186128)。  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>若要部署 MSI 中的 DSL  
  
1.  設定`InstalledByMsi`延伸模組資訊清單中。 這可防止 VSX 正在安裝和解除安裝 MSI 除外。 這很重要，如果您將 MSI 中包含其他元件。  
  
    1.  開啟 DslPackage\source.extension.tt  
  
    2.  插入下列這一行之前`<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  建立或編輯圖示，以代表您在 Windows 檔案總管的 DSL。 例如，編輯**DslPackage\Resources\File.ico**  
  
3.  請確定您的 DSL 的下列屬性正確︰  
  
    -   DSL 總管 中按一下根節點，然後在 屬性 視窗中，檢閱︰  
  
        -   說明  
  
        -   版本  
  
    -   按一下 **編輯器**節點，在 屬性 視窗中，按一下**圖示**。 將值設為參考中的圖示檔案**DslPackage\Resources**，例如**File.ico**  
  
    -   在**建置** 功能表上，開啟**Configuration Manager**，並選取您要建置的例如組態**版本**或**偵錯**。  
  
4.  移至[Visualization and Modeling SDK 首頁](http://go.microsoft.com/fwlink/?LinkID=186128)，以及從**下載**索引標籤上，下載**CreateMsiSetupProject.tt**。  
  
5.  新增**CreateMsiSetupProject.tt**至您的 Dsl 專案。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]將建立名為**CreateMsiSetupProject.vdproj**。  
  
6.  在 Windows 檔案總管 中，複製 Dsl\\*.vdproj 到新資料夾命名為安裝程式。  
  
     （如果您想，您可以立即排除 CreateMsiSetupProject.tt 從您的 Dsl 專案。）  
  
7.  在**方案總管 中**，加入**安裝\\\*.vdproj**為現有的專案。  
  
8.  在**專案**] 功能表上，按一下 [**專案相依性**。  
  
     在**專案相依性**對話方塊方塊中，選取 安裝專案。  
  
     選取此方塊旁邊**DslPackage**。  
  
9. 重建方案。  
  
10. 在 Windows 檔案總管 中，找出安裝專案中建立的 MSI 檔案。  
  
     將 MSI 檔案複製到您要安裝您的 DSL 的電腦。 按兩下 MSI 檔案。 執行安裝程式。  
  
11. 在目標電腦上，建立新的檔案具有您的 DSL 的副檔名。 確認︰  
  
    -   在 Windows 檔案總管 清單檢視中，檔案會顯示圖示與您所定義的描述。  
  
    -   當您按兩下檔案，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]正常啟動，且會在您的 DSL 編輯器中開啟 DSL 檔案。  
  
 如果想要的話，您可以在以手動方式，而不是使用文字範本中建立安裝專案。 包含此程序的逐步解說，請參閱第 5 章的[視覺化與模型 SDK 實驗室](http://go.microsoft.com/fwlink/?LinkId=208878)。  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>若要解除安裝 MSI 安裝 DSL  
  
1.  在 Windows 中，開啟**程式和功能**控制台。  
  
2.  解除安裝 DSL。  
  
3.  重新啟動 Visual Studio。
