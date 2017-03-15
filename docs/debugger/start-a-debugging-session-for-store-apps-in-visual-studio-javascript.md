---
title: "在 Visual Studio 中，為市集應用程式啟動偵錯工作階段 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.installedapppackagelauncher"
  - "vs.debug.error.wwahost_scriptdebuggingdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# 在 Visual Studio 中，為市集應用程式啟動偵錯工作階段 (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![適用於 Windows 和 Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 本主題說明如何對於開始對使用 JavaScript 和 HTML5 撰寫的 Windows 市集應用程式執行偵錯工作階段。您可以使用單一按鍵開始偵錯，也可以為特定案例設定偵錯工作階段，然後選擇應用程式的啟動方式。  
  
> [!NOTE]
>  對於使用 XAML 和 Visual C\#、Visual C\+\+ 或 Visual Basic 撰寫的應用程式，請參閱[啟動偵錯工作階段 \(VB、C\#、C\+\+ 和 XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a> 本主題內容  
 [本主題內容](#BKMK_In_this_topic)  
  
 [簡單的偵錯方法](#BKMK_The_easy_way_to_start_debugging)  
  
 [設定偵錯工作階段](#BKMK_Configure_the_debugging_session)  
  
-   [開啟專案的偵錯屬性頁](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [選擇組建組態選項](#BKMK_Choose_the_build_configuration_options)  
  
-   [選擇部署目標](#BKMK_Choose_the_deployment_target)  
  
-   [選擇要使用的偵錯工具](#BKMK_Choose_the_debugger_to_use)  
  
-   [(選擇性) 在偵錯工作階段中延遲啟動應用程式](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(選擇性) 停用網路回送](#BKMK__Optional__Disable_network_loopbacks)  
  
 [開始偵錯工作階段](#BKMK_Start_the_debugging_session)  
  
-   [開始偵錯 (F5)](#BKMK_Start_debugging__F5_)  
  
-   [開始偵錯 (F5)，但延遲啟動應用程式](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [在偵錯工具中啟動已安裝的應用程式](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [將偵錯工具附加至執行中的應用程式](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [將應用程式設定成以偵錯模式執行](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [附加偵錯工具](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> 簡單的偵錯方法  
 ![僅適用於 Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
1.  在 Visual Studio 中開啟應用程式方案。  
  
2.  如果解決方案包含適用於 Windows 市集應用程式和 Windows Phone 應用程式的專案，首先必須確定您要偵錯的專案為啟始專案。在方案總管中選取專案，然後從內容功能表選擇 \[設定為啟始專案\]。  
  
3.  按 F5。  
  
 ![僅適用於 Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Visual Studio 會建置並啟動已附加偵錯工具的應用程式。執行會持續到中斷點為止，若以手動方式暫停執行，就會發生未處理的例外狀況，或結束應用程式。如需詳細資訊，請參閱[快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)。  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> 設定偵錯工作階段  
 因為未編譯指令碼，所以不會套用組建組態與平台設定。如果您要對 C\+\+ 或 Managed 元件執行偵錯，請將 \[組態\] 設定為 \[偵錯\]，再從 \[組態\] 對話方塊中選擇目標平台。  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 開啟專案的偵錯屬性頁  
  
1.  在方案總管中選取專案。在捷徑功能表上選擇 \[屬性\]。  
  
2.  展開 \[組態屬性\] 節點，然後選擇 \[偵錯\]。  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> 選擇組建組態選項  
  
1.  從 \[組態\] 清單中，選擇 \[偵錯\] 或 \[作用中 \(偵錯\)\]。。  
  
2.  從 \[平台\] 清單中選擇建置的目標平台。在大部分情況下，\[任何 CPU\] 會是最佳選擇。  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> 選擇部署目標  
 您可以在 Visual Studio 電腦、本機電腦上的 Visual Studio 模擬器或遠端電腦上部署應用程式並對其執行偵錯。您可以從專案的 \[偵錯\] 屬性頁上之 \[要啟動的偵錯工具\] 清單中選擇目標。  
  
 ![僅適用於 Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 對於 Windows 市集應用程式，請從 \[目標裝置\] 清單中選擇下列其中一個選項：  
  
|||  
|-|-|  
|**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。請參閱[在本機電腦上執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-the-local-machine.md)。|  
|**模擬器**|在 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的 Visual Studio 模擬器中為應用程式執行偵錯。模擬器是可讓您對本機電腦上無法使用的裝置功能 \(例如觸控筆勢與裝置旋轉\) 進行偵錯的桌面視窗。請參閱[在模擬器中執行 Windows 市集應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|  
|**遠端電腦**|在透過內部網路連接到本機電腦的裝置上，或使用乙太網路纜線直接連接的裝置上，進行應用程式的偵錯。若要遠端偵錯，必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。請參閱[在遠端電腦上執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|  
  
 如果您選擇 \[遠端電腦\]，請以下列任一種方式指定遠端電腦的名稱或 IP 位址：  
  
-   在 \[電腦名稱\] 方塊中，輸入遠端電腦的名稱或 IP 位址。  
  
-   在 \[電腦名稱\] 方塊中選擇向下箭頭，然後選擇 \[\<尋找...\>\]。然後從 \[選取遠端偵錯工具連接\] 對話方塊中選擇遠端電腦。  
  
     ![選取遠端偵錯工具連接](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN\_PRO\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  \[選取遠端偵錯工具連接\] 對話方塊會顯示位於本機子網路上的電腦，以及透過乙太網路纜線直接連接至 Visual Studio 電腦的任何電腦。若要指定其他電腦，請在 \[電腦名稱\] 方塊中輸入名稱。  
  
 ![僅適用於 Windows Phone](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 對於 Windows Phone 應用程式，請選擇 \[裝置\]，或從 \[目標裝置\] 清單中選擇一個模擬器。  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> 選擇要使用的偵錯工具  
 偵錯工具預設會附加到您應用程式中的 JavaScript 程式碼。您可以選擇偵錯您應用程式元件的原生 C\+\+ 和 Managed 程式碼，而非 JavaScript 程式碼。在應用程式專案之 \[偵錯\] 屬性頁的 \[偵錯工具類型\] 清單中，指定要執行偵錯的程式碼。  
  
 請從 \[偵錯工具類型\] 清單中選擇一個偵錯工具：  
  
|||  
|-|-|  
|**僅限指令碼**|對應用程式中的 JavaScript 程式碼執行偵錯。Managed 程式碼與原生碼會予忽略。|  
|**僅限原生**|對應用程式中的原生 C\/C\+\+ 程式碼執行偵錯。Managed 程式碼與 JavaScript 程式碼會予忽略。|  
|**機器碼加指令碼**|在您的應用程式中對原生 C\+\+ 程式碼與 JavaScript 程式碼執行偵錯。|  
|**僅限 Managed**|對應用程式中的 Managed 程式碼執行偵錯。JavaScript 程式碼與原生 C\/C\+\+ 程式碼會予忽略。|  
|**混合 \(Managed 與原生\)**|對應用程式中的原生 C\/C\+\+ 程式碼與 Managed 程式碼執行偵錯。JavaScript 程式碼會予忽略。|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> \(選擇性\) 在偵錯工作階段中延遲啟動應用程式  
 Visual Studio 預設會在您開始進行偵錯時，立即啟動該應用程式。您也可以僅開始偵錯工作階段，而延遲啟動您的應用程式。如果從 \[開始\] 功能表或由啟用合約啟動應用程式，或是由其他處理序或方法啟動應用程式，即會在偵錯工具中啟動應用程式。您也可以使用延遲啟動，來偵錯應用程式中想要在應用程式未執行時發生的背景事件。  
  
 您可以在應用程式專案的 \[偵錯\] 屬性頁之 \[啟動應用程式\] 清單中，指定是否要延遲啟動應用程式。選擇下列任一選項：  
  
-   選擇 \[否\] 會延遲啟動您的應用程式。  
  
-   選擇 \[是\] 會立即啟動您的應用程式。  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(選擇性\) 停用網路回送  
 ![僅適用於 Windows](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 基於安全性的理由，以標準形式安裝的 Windows 市集應用程式，不得對其安裝所在的裝置進行網路呼叫。根據預設，Visual Studio 部署會針對部署應用程式建立此規則的豁免。此豁免可讓您測試在單一機器上的通訊程序。將應用程式提交到 Windows 市集之前，應不使用豁免來測試您的應用程式。  
  
 若要移除網路回送豁免，請從 \[偵錯\] 屬性頁的 \[允許網路回送\] 清單中選擇 \[否\] 。  
  
##  <a name="BKMK_Start_the_debugging_session"></a> 開始偵錯工作階段  
  
###  <a name="BKMK_Start_debugging__F5_"></a> 開始偵錯 \(F5\)  
 當您從 \[偵錯\] 功能表上選擇 \[開始偵錯\] 時 \(鍵盤：**F5**\)，Visual Studio 會啟動附加有偵錯工具的應用程式。執行會持續到出現中斷點為止，若以手動方式暫止執行，會發生未處理的例外狀況，或結束應用程式。  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 開始偵錯 \(F5\)，但延遲啟動應用程式  
 您可以將應用程式設定成以偵錯模式執行，但使用偵錯工具以外的方法啟動。例如，您可能會希望從 \[開始\] 功能表啟動應用程式時即執行偵錯，或對應用程式的背景處理序執行偵錯，而不啟動應用程式。若要延遲啟動應用程式，請執行下列作業：  
  
1.  在應用程式專案屬性的 \[偵錯\] 頁面上，從 \[啟動應用程式\] 清單中選擇 \[否\]。  
  
2.  從 \[偵錯\] 功能表上選擇 \[開始偵錯\] \(鍵盤：F5\)。  
  
3.  從 \[開始\] 功能表、執行合約或透過其他處理序，啟動您的應用程式。  
  
 該應用程式會以偵錯模式啟動。執行會持續到出現中斷點為止，若以手動方式暫止執行，會發生未處理的例外狀況，或結束應用程式。  
  
 如需偵錯背景工作的詳細資訊，請參閱[觸發、暫停和繼續事件，以及讓事件成為背景事件 \(Windows 市集\)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 在偵錯工具中啟動已安裝的應用程式  
 使用 F5 開始偵錯時，Visual Studio 會建置及部署應用程式、將應用程式設定為以偵錯模式執行，然後再啟動該應用程式。若要啟動已安裝在裝置上的應用程式，請使用 \[偵錯已安裝的應用程式套件\] 對話方塊。當您必須偵錯從 Windows 市集安裝的應用程式，或者有應用程式的原始程式檔，卻沒有應用程式的 Visual Studio 專案時，這個方式就很有用。例如，您可能有並非使用 Visual Studio 專案或方案所建置的自訂系統。  
  
 該應用程式可安裝在本機裝置，或其可在遠端裝置上。您可以立即啟動應用程式，也可以設定應用程式，使其藉由其他處理序或方式啟動 \(例如從 \[開始\] 功能表或透過啟用合約\) 後再於偵錯工具中執行。如果您只希望偵錯背景處理程序而不啟動應用程式，還可以將應用程式設定成以偵錯模式執行。如需詳細資訊，請參閱[觸發、暫停和繼續事件，以及讓事件成為背景事件 \(Windows 市集\)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)。  
  
 若要將已安裝的應用程式設定為在偵錯模式下執行，請執行這項操作：  
  
> [!NOTE]
>  當您啟動此程序時，不得執行此應用程式。  
  
1.  在 \[偵錯\] 功能表上，選擇 \[偵錯已安裝的應用程式套件\]。  
  
2.  從清單中選擇下列任一選項：  
  
    |||  
    |-|-|  
    |**本機電腦**|在本機電腦上對目前工作階段中的應用程式進行偵錯。請參閱[在本機電腦上執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-the-local-machine.md)。|  
    |**模擬器**|在 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的 Visual Studio 模擬器中為應用程式執行偵錯。模擬器是可讓您對本機電腦上無法使用的裝置功能 \(例如觸控筆勢與裝置旋轉\) 進行偵錯的桌面視窗。請參閱[在模擬器中執行 Windows 市集應用程式](../debugger/run-windows-store-apps-in-the-simulator.md)。|  
    |**遠端電腦**|在透過內部網路連接到本機電腦的裝置上，或使用乙太網路纜線直接連接的裝置上，進行應用程式的偵錯。若要遠端偵錯，必須在遠端裝置上安裝並執行 Visual Studio 遠端工具。請參閱[在遠端電腦上執行 Windows 市集應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)。|  
  
3.  從 \[已安裝的應用程式套件\] 清單中選擇應用程式。  
  
4.  從 \[偵錯這種程式碼類型\] 清單中，選擇要使用的偵錯引擎。  
  
5.  \(選擇性\)。選擇 \[不啟動，但在我的程式碼啟動時進行偵錯\]，如此當以其他方法啟動應用程式時，即會偵錯該應用程式，或是偵錯背景處理程序。  
  
 當您按一下 \[開始\] 時，就會啟動應用程式，或將其設定成以偵錯模式執行。  
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 將偵錯工具附加至執行中的應用程式  
 若要將偵錯工具附加到 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式，必須使用 \[Debuggable Package 管理員\] 將應用程式設定為以偵錯模式執行。\[Debuggable Package 管理員\] 會隨 Visual Studio 遠端工具一起安裝。  
  
 當您需要對已安裝的應用程式 \(例如從 Windows 市集安裝的應用程式\) 執行偵錯時，將偵錯工具附加至應用程式將會有所幫助。當您具有應用程式的原始程式檔，但沒有應用程式的 Visual Studio 專案時，就必須進行附加。例如，您可能會有未使用 Visual Studio 專案或方案的自訂建置系統。  
  
 若要附加至應用程式：  
  
1.  將應用程式設定成以偵錯模式執行此動作必須在未執行應用程式時完成。  
  
2.  啟動應用程式。您可以從 \[開始\] 功能表、執行合約或透過其他方法啟動應用程式。  
  
3.  將偵錯工具附加至執行中的應用程式。  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> 將應用程式設定成以偵錯模式執行  
  
1.  在已安裝應用程式的裝置上，安裝 Visual Studio 遠端工具。請參閱[安裝遠端工具](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)。  
  
2.  在 \[開始\] 功能表上搜尋 `Debuggable Package Manager` 並加以啟動。  
  
     為 AppxDebug Cmdlet 設定的 PowerShell 視窗會隨即出現。  
  
3.  若要啟用應用程式的偵錯功能，您必須指定此應用程式的 PackageFullName 識別項。若要檢視包含 PackageFullName 的完整應用程式清單，請在 PowerShell 命令提示字元處輸入 `Get-AppxPackage`。  
  
4.  在 PowerShell 命令提示字元中，輸入`Enable-AppxDebug` *PackageFullName*，而其中的 *PackageFullName* 是應用程式的 PackageFullName 識別項。  
  
###  <a name="BKMK_Attach_the_debugger"></a> 附加偵錯工具  
  
> [!TIP]
>  JavaScript 應用程式會在 wwahost.exe 處理序的執行個體中執行。如果在您附加至應用程式時有其他 JavaScript 應用程式正在執行，則需要知道在其中執行應用程式之 wwahost.exe 的數值處理序 ID \(PID\)。  
>   
>  此狀況最簡單的處理方式，就是關閉所有其他 JavaScript 應用程式。否則，您可以在啟動應用程式之前開啟 Windows 工作管理員，並記下 wwahost.exe 處理序的 ID。當您在 \[可使用的處理序\] 對話方塊中，指定要附加的處理序時，應用程式之 wwahost.exe 的 ID 將會不同於您所記下的 ID。  
  
 若要附加偵錯工具：  
  
1.  在 \[偵錯\] 功能表上，選擇 \[附加至處理序\]。  
  
     \[附加至處理序\] 對話方塊會隨即出現。  
  
2.  若要附加至遠端裝置上的應用程式，請在 \[限定詞\] 方塊中指定遠端裝置。您可以：  
  
    -   在 \[限定詞\] 方塊中輸入名稱。  
  
    -   選擇 \[限定詞\] 方塊中的向下箭頭，並從您先前附加之裝置的清單中選擇裝置。  
  
    -   選擇 \[尋找\]，以從本機子網路上的裝置清單中選取裝置。  
  
3.  在 \[附加至\] 方塊中指定您要偵錯的程式碼類型。  
  
     選擇 \[選取\]，然後執行下列其中一項動作：  
  
    -   選擇 \[自動判斷要偵錯的程式碼類型\]  
  
    -   選擇 \[偵錯這些程式碼類型\]，然後從清單中選擇一或多個類型。  
  
4.  在 \[可使用的處理序\] 清單中，選擇適當的 **wwahost.exe** 處理序。使用 \[標題\] 資料行識別您的應用程式。  
  
5.  選擇 \[附加\]。  
  
 Visual Studio 會將偵錯工具附加至處理序。執行會持續到出現中斷點為止，若以手動方式暫止執行，會發生未處理的例外狀況，或結束應用程式。  
  
## 請參閱  
 [在偵錯工作階段中控制執行 \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)   
 [觸發、暫停和繼續事件，以及讓事件成為背景事件 \(Windows 市集\)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [在 Visual Studio 中偵錯應用程式](../debugger/debug-store-apps-in-visual-studio.md)