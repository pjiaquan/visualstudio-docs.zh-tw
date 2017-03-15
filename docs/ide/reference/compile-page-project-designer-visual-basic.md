---
title: "專案設計工具、編譯頁 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "編譯，Visual Basic 專案"
  - "編譯，選項 [Visual Basic]"
  - "編譯器，Visual Basic 選項"
  - "編譯，指示 [Visual Basic]"
  - "編譯器選項，Visual Basic"
  - "專案設計工具，編譯頁"
  - "專案設計工具中的編譯頁"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# 專案設計工具、編譯頁 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用 \[專案設計工具\] 的 \[**編譯**\] 頁，指定編譯指令。  您也可以在此指定進階編譯器選項及建置前或建置後事件。  
  
 若要存取 \[**編譯**\] 頁，請選取專案節點 \(不是 \[**方案**\] 節點\) 在 \[**方案總管**\]。  然後選取 \[**專案**\]，請在功能表列上的 \[**屬性**\] 。  顯示 \[專案設計工具\] 時，請按一下 \[**編譯**\] 索引標籤。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 組態和平台  
 以下設定可讓您選取要顯示或要修改的組態和平台。  
  
> [!NOTE]
>  使用簡化組建組態，專案系統會判斷要建置偵錯或發行版本。  因此沒有顯示 \[**組態**\] 和 \[**平台**\] 清單。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
 **組態**  
 指定要顯示或修改的組態設定。  設定為 \[**偵錯**\] \(預設值\)、\[**發行**\] 或 \[**所有組態**\]。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)與[如何：建立和編輯組態](../../ide/how-to-create-and-edit-configurations.md)。  
  
 **平台**  
 指定要顯示或修改的平台設定。  您可以指定 \[**任何 CPU**\] \(預設值\)， \[ \[**x64**\] 或 \[**x86**\]。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
## 編譯器組態選項  
 下列設定可讓您設定編譯器組態選項。  
  
 **建置輸出路徑**  
 指定此專案組態的輸出檔案位置。  在這個方塊中輸入建置輸出路徑，或者按一下 \[**瀏覽**\] 按鈕以選取路徑。  請注意，路徑是相對的，如果您輸入絕對路徑，它會儲存成相對路徑。  預設路徑為 bin\\Debug\\ 或 bin\\Release\\。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
 使用簡化組建組態，專案系統會判斷要建置偵錯或發行版本。  不論您所指定的 \[**輸出路徑**\] 為何，\[**偵錯**\] 功能表 \(F5\) 上的 \[**建置**\] 命令，就會將組建放在偵錯位置中。  但是，使用 \[**建置**\] 功能表上的 \[**建置**\] 命令卻會放在您所指定的位置。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
 **Option Explicit**  
 指定是否允許變數隱含宣告。  選取 \[**開**\]，要求明確宣告變數。  如果變數未在使用前宣告，這會導致編譯器報告錯誤。  如果選取 \[**Off**\]，則可以用隱含方式宣告變數。  
  
 這個設定對應於 [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) 編譯器選項。  
  
 如果原始碼檔案包含[Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)，陳述式中的 `On` 或`Off` 值會覆寫 \[**編譯頁面**\] 中的 \[**選項明確**\] 設定。  
  
 當您建立新專案時，\[**編譯**\] 頁上的 \[**Option Explicit**\] 會設定為 \[**選項**\] 對話方塊中的 \[**Option Explicit**\] 設定值。  若要檢視或變更這個對話方塊中的設定，請按一下 \[**工具**\] 功能表中的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  在 \[**VB 預設值**\] 中的 \[**Option Explicit**\] 初始預設設定是 \[**On**\]。  
  
 將 \[**Option Explicit**\] 設定為 `Off` 通常不是好做法。  一個或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。  
  
 **Option Strict**  
 指定是否強制執行嚴格的類型語意。  當 \[**Option Strict**\] 為 \[**On**\] 時，下列情況將造成編譯時期錯誤：  
  
-   隱含 Narrowing 轉換  
  
-   晚期繫結  
  
-   造成 `Object`類型的隱含類型化  
  
 隱含資料類型轉換是 Narrowing 轉換時，會發生隱含 Narrowing 轉換錯誤。  如需詳細資訊，請參閱 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)、[Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)和[Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)。  
  
 物件被指派給宣告類型為 `Object` 之變數的屬性或方法時，為晚期繫結物件。  如需詳細資訊，請參閱[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)與[Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)。  
  
 無法推斷宣告變數的適當類型，因此推斷`Object`類型時，會發生隱含物件類型錯誤。  這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。  如需詳細資訊，請參閱[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)、[Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) 和 [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification)。  
  
 \[**Option Strict**\] 設定對應至 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 編譯器選項。  
  
 如果原始碼檔案包含[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)，陳述式中的 `On` 或`Off` 值會覆寫 \[**編譯頁面**\]中的 \[**選項嚴格**\] 設定。  
  
 當您建立專案時，\[**編譯**\] 頁上的 \[**Option Strict**\] 設定會設定為 \[**選項**\] 對話方塊中 \[**Option Strict**\] 的值。  若要檢視或變更這個對話方塊中的設定，請按一下 \[**工具**\] 功能表中的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  在 \[**VB 預設值**\] 中的 \[**Option Strict**\] 初始預設設定是 \[**Off**\]。  
  
 **選項嚴格個別警告。**\[**編譯**\] 頁的 \[**警告組態**\] 區段中所包含的設定對應三個會在 `Option Strict` 設為開啟時導致編譯時期錯誤的條件。  以下是這些設定：  
  
-   **隱含轉換**  
  
-   **後期繫結；叫用可能會在執行階段失敗**  
  
-   **隱含類型；假定物件**  
  
 當您將 \[**Option Strict**\] 設定為 \[**開啟**\] 時，這三個警告組態設定都會設定為 \[**錯誤**\]。  當您將 \[**Option Strict**\] 設定為 \[**關閉**\] 時，所有三個設定都會設定為 \[**無**\]。  
  
 您可以將每個警告組態個別變更為 \[**無**\]、\[**警告**\] 或 \[**錯誤**\]。  如果三個警告組態設定皆設為 \[**錯誤**\]，`On`會出現在`Option strict`方塊中。  如果三個都設為 \[**無**\]，此方塊中會出現  `Off`。  若為這些設定的其他任何組合，會出現 \[**\(自訂\)**\]。  
  
 **Option Compare**  
 指定要使用的字串比較型別。  選擇 \[**二進位**\]，指示編譯器使用二進位、區分大小寫的字串比較。  選取 \[**文字**\]，則會使用依地區設定特性 \(Locale\-Specific\)、不區分大小寫的文字字串比較。  
  
 這個設定對應於 [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) 編譯器選項。  
  
 如果原始碼檔案包含[Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement)，陳述式中的 `Binary`或`Text`會覆寫 \[**編譯頁面**\] 中的 \[**選項比較**\] 設定。  
  
 當您建立專案時，\[**編譯**\] 頁上的 \[**Option Compare**\] 設定會設定為 \[**選項**\] 對話方塊中 \[**Option Compare**\] 的值。  若要檢視或變更這個對話方塊中的設定，請按一下 \[**工具**\] 功能表中的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  在 \[**VB 預設值**\] 中的 \[**Option Compare**\] 初始預設設定是 \[**Binary**\]。  
  
 **Option infer**  
 指定變數宣告中是否允許區域型別推斷。  選取 \[**開**\]，允許使用區域型別推斷。  選取 \[**Off**\] 以攔阻區域型別推斷。  
  
 這個設定對應於 [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) 編譯器選項。  
  
 如果原始碼檔案包含[Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)，陳述式中的 `On` 或`Off` 值會覆寫 \[**編譯頁面**\] 中的 \[**選項推斷**\] 設定。  
  
 當您建立專案時，\[**編譯**\] 頁上的 \[**Option Infer**\] 設定會設定為 \[**選項**\] 對話方塊中 \[**Option Infer**\] 的值。  若要檢視或變更這個對話方塊中的設定，請按一下 \[**工具**\] 功能表中的 \[**選項**\]。  在 \[**選項**\] 對話方塊中，展開 \[**專案和方案**\]，然後按一下 \[**VB 預設值**\]。  在 \[**VB 預設值**\] 中的 \[**Option Infer**\] 初始預設設定是 \[**On**\]。  
  
 **目標 CPU**  
 指定做為輸出檔目標的處理器。  為所有 32 位元 Intel 相容處理器指定任何 64 位元 Intel 相容處理器的 \[**x86**\] 時，任何 ARM 處理器的 \[**x64**\] ， \[**ARM**\] 或 \[**任何 CPU**\] 指定任何處理器是可接受的。  因為它在硬體類型，最多可讓應用程式執行 \[**任何 CPU**\] 是新專案的預設值。  
  
 如需詳細資訊，請參閱[\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform)。  
  
 \[**32 位元的慣用方法。**\]  
 如果 \[**Prefer32 位元**\] 核取方塊已選取，應用程式設定為在 Windows 32 位元和 64 位元版本的 32 位元應用程式。  否則，應用程式設定為在 Windows 32 位元版本的 32 位元應用程式和做為 Windows 64 位元版本的 64 位元應用程式。  
  
 執行，因為 64 位元應用程式加倍指標大小及其可能產生相容性問題完整 32 位元的型別程式庫。  其執行速度本機執行或需要超過 4 GB 記憶體，因此才會執行應用程式如 64 位元。  
  
 只有在下列所有條件都成立時，這個核取方塊可用:  
  
-   在 \[**編譯頁面**\] 中， \[ \[**目標 CPU**\] 清單設定為 \[**任何 CPU**\]。  
  
-   在 \[**應用程式頁面**\] 中， \[ \[**應用程式類型**\] 清單指定專案是應用程式。  
  
-   在 \[**應用程式頁面**\] 中， \[ \[**目標 Framework**\] 清單指定 .NET Framework 4.5。  
  
 **警告組態**  
 這個表格會列出建置條件以及各項條件所對應之 \[**無**\]、\[**警告**\] 或 \[**錯誤**\] 的告知層級。  
  
 根據預設，所有的編譯器警告都會在進行編譯時加入到工作清單中。  選取 \[**停用所有警告**\]，以指示編譯程式不要發出警告或錯誤。  如果您要編譯器將警告視為必須修正的錯誤，選取 \[**將所有警告視為錯誤**\]。  
  
 **停用所有警告**  
 指定是否允許編譯器發出通知，如本文件稍早的「**狀況與告知**」表中的描述。  這個核取方塊預設為清除。  如果選取這個核取方塊，則會指示編譯器不要發出警告或錯誤。  
  
 這個設定對應於 [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 編譯器選項。  
  
 **將所有警告都視為錯誤。**  
 指定如何看待警告。  這個核取方塊預設為清除，也就是所有警告通知仍然設定為 \[**警告**\]。  選取這個核取方塊，則會將所有警告通知變更為 \[**錯誤**\]。  
  
 只有在清除 \[**停用所有警告**\] 的情況下，才能使用這個選項。  
  
 **產生 XML 文件檔案**  
 指定是否產生文件資訊。  這個核取方塊預設為選取，指示編譯器產生文件資訊並放在 XML 檔案中。  如果清除這個核取方塊，就會指示編譯器不要建立文件。  
  
 這個設定對應於 [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) 編譯器選項。  
  
 **註冊 COM Interop**  
 指定 Managed 應用程式是否要公開 COM 物件 \(COM 可呼叫包裝函式\)，讓 COM 物件與應用程式互動。  
  
 這個核取方塊預設為清除，也就是指定應用程式不允許 COM Interop。  如果選取這個核取方塊，則允許使用 COM Interop。  
  
 這個選項不適用於 \[Windows 應用程式\] 或 \[主控台應用程式\] 專案。  
  
 **建置事件**  
 按一下這個按鈕以存取 \[**建置事件**\] 對話方塊。  使用這個對話方塊以指定專案的建置前和建置後組態指令。  此對話方塊只適用於 Visual Basic 專案。  如需詳細資訊，請參閱[建置事件對話方塊 \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md)。  
  
 **進階編譯選項**  
 按一下這個按鈕以存取 \[**進階 編譯器設定**\] 對話方塊。  使用 \[**進階 編譯器設定**\] 對話方塊，指定專案的進階組建組態屬性。  此對話方塊只適用於 Visual Basic 專案。  如需詳細資訊，請參閱[進階編譯器設定對話方塊 \(Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)。  
  
## 請參閱  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/zh-tw/94308881-f10f-4caf-a729-f1028e596a2c)   
 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [如何：建立和編輯組態](../../ide/how-to-create-and-edit-configurations.md)