---
title: "Visual Studio 中的 Just-In-Time 偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], Just-In-Time"
  - "Just-In-Time 偵錯"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visual Studio 中的 Just-In-Time 偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當 Visual Studio 外執行的應用程式發生例外狀況或沒有回應時，Just\-in\-Time 偵錯會自動啟動 Visual Studio。  這樣可讓您在 Visual Studio 未執行的情況下測試應用程式，並於發生問題時使用 Visual Studio 開始偵錯。  
  
 Just\-In\-Time 偵錯不適用於 Windows 市集應用程式。  Just\-In\-Time 偵錯無法在原生應用程式 \(例如視覺化檢視\) 中所裝載的 Managed 程式碼上運作。  
  
## 使用 Just\-In\-Time 偵錯  
 當您安裝 Visual Studio 時，預設會啟用 Just\-In\-Time 偵錯。  如果您需要停用或重新啟用 Just\-In\-Time 偵錯，請參閱[將逐步執行限制於 Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 當 Just\-In\-Time 偵錯啟用時，您可以在 Visual Studio 外測試應用程式。  在沒有回應或發生例外狀況時，您會看到具有類似下列訊息的對話方塊：  
  
 在 terrarium.exe\[3384\] 中發生未處理的例外狀況 \('System.TypeInitializationException'\)。  
  
 出現這個對話方塊時，您可以使用下列程序開始偵錯。  
  
#### 若要在發生錯誤時開始進行 Just\-In\-Time 偵錯  
  
1.  在 \[Just\-In\-Time 偵錯\] 對話方塊的 \[可能的偵錯工具\] 清單中，按一下 \[Visual Studio 2015 的新執行個體\]，或按一下已在執行中的 Visual Studio 執行個體。  
  
2.  若要針對所有未來的損毀自動使用 Visual Studio，請按一下 \[**將目前所選取的偵錯工具設定為預設的偵錯工具**\]。  
  
3.  如果想要選擇能夠對何種程式碼類型進行偵錯，請按一下 \[**手動選擇偵錯引擎**\]。  如果沒有選擇這個選項，Visual Studio 就會自動根據程式中的程式碼類型，選擇適當的偵錯引擎。  
  
4.  按一下 \[**確定**\]。  
  
5.  如果應用程式包含的組件含有不受信任的程式碼，就會出現安全性警告對話方塊。  這個對話方塊可讓您決定是否繼續偵錯。  在繼續偵錯之前，請決定這是否為可以信任的程式碼。  這是您自行撰寫的程式碼嗎？  您信任撰寫這個程式碼的人嗎？  如果應用程式在遠端電腦上執行，您認得它的處理序名稱嗎？  即使應用程式在本機執行，也不代表絕對可以信任。  例如，惡意的 ActiveX 控制項有可能會在 Internet Explorer 中執行。  不要忽視電腦上執行這類惡意程式碼的可能性。  如果確定可以信任您要偵錯的程式碼，請按一下 \[**偵錯**\]。  否則，請按一下 \[**不要偵錯**\]。  
  
##  <a name="BKMK_Enabling"></a> 啟用或停用 Just\-In\-Time 偵錯  
 您可以從 \[**選項**\] 對話方塊啟用或停用 Just\-In\-Time 偵錯。  
  
#### 若要啟用或停用 Just\-In\-Time 偵錯  
  
1.  在 \[**工具**\] 功能表上按一下 \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中選取 \[**偵錯**\] 資料夾。  
  
3.  在 \[**偵錯**\] 資料夾中選取 \[**Just\-In\-Time**\] 頁面。  
  
4.  在 \[**啟用這些程式碼類型的 Just\-In\-Time 偵錯**\] 方塊中，選取或清除相關的程式類型：\[**Managed**\]、\[**原生**\] 或 \[**指令碼**\]。  
  
     若要在啟用 Just\-In\-Time 偵錯之後加以停用，您必須以系統管理員權限執行。  啟用 Just\-In\-Time 偵錯會設定一個登錄機碼，您必須使用系統管理員權限才能變更該機碼。  
  
5.  按一下 \[**確定**\]。  
  
 根據預設，Windows Form 應用程式具有最上層的例外狀況處理常式，允許程式在能夠復原時繼續執行。  因此，您必須執行下列額外步驟，才能對 Windows Form 應用程式啟用 Just\-In\-Time 偵錯。  
  
#### 若要啟用 Windows Form 的 Just\-In\-Time 偵錯  
  
1.  在 machine.config 或 `jitDebugging`application.exe.config 檔案的 `true` 區段中，將 `system.windows.form` 值設為 *：*  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  在 C\+\+ Windows Form 應用程式中，您也必須在 .config 檔或您的程式碼中設定 `DebuggableAttribute`。  如果您使用 [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) 而且未使用 [\/Og](/visual-cpp/build/reference/og-global-optimizations) 進行編譯，則編譯器將會設定這個屬性 \(Attribute\)。  然而，如果您要對非最佳化的發行組建進行偵錯，則必須自行完成此設定。  若要這樣做，您可以將下面這行程式碼加入至應用程式的 AssemblyInfo.cpp 檔案。  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     如需詳細資訊，請參閱<xref:System.Diagnostics.DebuggableAttribute>。  
  
 即使電腦上已沒有安裝 Visual Studio，Just\-In\-Time 偵錯可能仍然為啟用狀態。  當 Visual Studio 未安裝時，您無法從 Visual Studio \[**選項**\] 對話方塊停用 Just\-In\-Time 偵錯。  在此情況下，您可以編輯 Windows 登錄來停用 Just\-In\-Time 偵錯。  
  
#### 若要編輯登錄來停用 Just\-In\-Time 偵錯  
  
1.  在 \[**開始**\] 功能表中，搜尋並執行 `regedit.exe`  
  
2.  在 \[**登錄編輯程式**\] 視窗中，尋找並刪除下列登錄機碼：  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  如果您的電腦執行 64 位元作業系統，也請刪除下列登錄機碼：  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  請小心不要刪除或變更其他任何登錄機碼。  
  
5.  關閉 \[**登錄編輯程式**\] 視窗。  
  
## Just\-In\-Time 偵錯的錯誤  
 您可能會看見下列與 Just\-in\-Time 偵錯相關的錯誤訊息。  
  
-   **無法附加至沒有回應的處理序。  所指定的程式不是 Windows 或 MS\-DOS 程式。**  
  
     當您試圖附加至在 Windows 2000 以另一個使用者身分執行的處理序時，就會發生這個錯誤。  
  
     若要解決這個問題，請啟動 Visual Studio，從 \[**偵錯**\] 功能表開啟 \[**附加至處理序**\] 對話方塊，然後在 \[**可使用的處理序**\] 清單中找出您要偵錯的處理序。  如果您不知道處理序的名稱，請查看 \[**Visual Studio Just\-In\-Time 偵錯工具**\] 對話方塊，然後記下處理序 ID。  在 \[**可使用的處理序**\] 清單中選取該處理序，然後按一下 \[**附加**\]。  在 \[**Visual Studio Just\-In\-Time 偵錯工具**\] 對話方塊中，按一下 \[**否**\] 以關閉此對話方塊。  
  
-   **因為沒有使用者登入導致無法啟動偵錯工具。**  
  
     當 Just\-In\-Time 偵錯嘗試在沒有使用者登入主控台的電腦上啟動 Visual Studio 時，就會發生此錯誤。  因為沒有使用者登入，所以沒有使用者工作階段可顯示 \[Just\-In\-Time 偵錯\] 對話方塊。  
  
     若要修正這個問題，請登入該電腦。  
  
-   **類別未登錄。**  
  
     這個錯誤表示偵錯工具嘗試建立的 COM 類別尚未登錄，可能是因為安裝問題所致。  
  
     若要修正這個問題，請使用安裝磁碟重新安裝或修復 Visual Studio 安裝。  
  
## 請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [選項對話方塊、偵錯、Just\-In\-Time](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [安全性警告：附加至未受信任的使用者帳戶所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)