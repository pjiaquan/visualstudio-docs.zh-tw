---
title: "疑難排解 VSPackages |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
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
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>疑難排解 Vspackage
以下是常見的問題，您可能遇到的 VSPackage 秘訣來解決問題。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>若要疑難排解防止 Visual Studio 啟動的 VSPackage  
  
-   啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以安全模式。  
  
     若要啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在安全模式中，在命令提示字元中，輸入**devenv.exe /safemode**。  
  
     此程序期間沒有 VSPackages 載入除了隨附於 VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>若要疑難排解不會載入 VSPackage  
  
1.  請確定您使用註冊通常執行的實驗性的登錄根目錄 VSPackage 的登錄根目錄。  
  
     如需詳細資訊，請參閱[實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
2.  如果 VSPackage 的目標在實驗性的登錄根目錄中執行，請確定您正在執行的實驗版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     若要執行的實驗版本，請在命令視窗中輸入下列︰ **devenv /rootsuffix exp**。  
  
3.  請檢查您的 VSPackage 登錄項目。  
  
     如需詳細資訊，請參閱[註冊 VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)和[管理 VSPackages](../extensibility/managing-vspackages.md)。  
  
4.  開啟**輸出** 視窗中的執行個體的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，無法載入 VSPackage。 資訊載入 VSPackage 失敗的原因可能會顯示該視窗中。  
  
    > [!NOTE]
    >  如果您要啟動的實驗版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)，檢查**輸出** 視窗中的兩個版本。  
  
5.  檢查活動記錄檔。  
  
     如需詳細資訊，請參閱[How to︰ 使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
6.  如需有關 IDE 所擲回的例外狀況的詳細資訊，請按一下 **例外狀況**上**偵錯**功能表啟用例外狀況。 在**例外狀況** 對話方塊中選取想要有關的詳細資訊的例外狀況的類型。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>若要疑難排解不會註冊 VSPackage  
  
1.  請確定 VSPackage 組件所在的受信任位置。 RegPkg 無法在不信任或部分信任的位置，例如網路共用的預設.net 安全性組態中註冊組件。 雖然每當使用者在不受信任的位置中建立專案時，會出現警告，「 不要顯示此訊息一次 」 的核取方塊可以避免發生此警告訊息。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>若要疑難排解，看不到或，會產生錯誤，當您按一下命令的命令  
  
1.  合併的新增或變更功能表命令以及已在 IDE 中，輸入下列內容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示字元︰ **devenv /rootsuffix Exp /setup**。  
  
2.  請確定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以找到 UI.dll VSPackage。  
  
    1.  在登錄的 [套件] 區段中找到 VSPackage 的 CLSID:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\Packages  
  
    2.  請確認 SatelliteDll 子機碼所指定的路徑正確。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>若要疑難排解非預期的行為的 VSPackage  
  
1.  在您的程式碼中設定中斷點。  
  
     偵錯很好的起點是建構函式和初始設定方法。 您也可以在您想要評估，例如功能表命令區域中設定中斷點。 若要啟用中斷點，您必須偵錯工具下執行。  
  
    1.  在**專案**] 功能表上，按一下 [**屬性**。  
  
    2.  在**屬性頁**對話方塊中，選取**偵錯** 索引標籤。  
  
    3.  在**命令列引數**方塊中，輸入在開發環境的根尾碼的 VSPackage 目標。 例如，若要選取實驗組建中，輸入︰ **RootSuffix Exp**。  
  
    4.  在**偵錯**] 功能表上，按一下 [**開始偵錯**或按 F5。  
  
        > [!NOTE]
        >  如果您正在偵錯的專案，建立或立即載入專案的現有執行個體。  
  
2.  使用活動記錄檔。  
  
     追蹤資訊寫入活動記錄在關鍵點 VSPackage 行為。 當您執行 VSPackage 零售環境中，這項技術會特別有用。 如需詳細資訊，請參閱[How to︰ 使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。  
  
3.  使用公用符號。  
  
     若要改善可讀性偵錯時，您可以附加至偵錯工具的符號。  
  
    1.  從**工具/選項** 功能表上，瀏覽至**偵錯/符號**對話方塊。  
  
    2.  加入下列**符號檔 (.pdb) 位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  若要改善效能，例如指定符號快取資料夾︰  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>若要疑難排解遺漏 VSPackage 或其中一個相依性  
  
1.  Managed 程式碼，請確定參考路徑正確無誤。  
  
    1.  在**專案**] 功能表上，按一下 [**屬性**。  
  
    2.  選取**參考**索引標籤中**屬性頁** 對話方塊中，並確定所有路徑都是否正確。 或者，您可以使用**物件瀏覽器**瀏覽參照的物件。  
  
         Managed 程式碼，您可以使用[Fuslogvw.exe （組件繫結記錄檔檢視器）](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296)顯示失敗的組件載入的詳細資料。  
  
2.  Unmanaged 程式碼中，找到的 VSPackage 中 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID 登錄節點︰  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\CLSID  
  
 請確定 InprocServer32 項目具有正確的 VSPackage dll 的路徑。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage](../extensibility/internals/vspackages.md)
