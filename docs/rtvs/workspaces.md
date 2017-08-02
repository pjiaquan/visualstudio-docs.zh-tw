---
title: "Visual Studio R 工具中的工作區 | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: zh-tw
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>控制 R 程式碼以工作區執行的位置

Visual Studio R 工具 (RTVS) 的工作區可讓您設定 R 工作階段的執行位置，此位置可能位於本機和遠端電腦。 目標是讓您以可比較性的使用者體驗在任一電腦上運作，讓您能夠充分利用可能更強大的雲端型電腦。

若要開啟 [工作區] 視窗，請使用 [R 工具] > [Windows] > [工作區] 命令，或按 Ctrl+9。

![Visual Studio R 工具的工作區視窗 (VS2017)](~/docs/rtvs/media/workspaces-window.png)

在此視窗中，綠色的核取記號表示 RTVS 繫結所在的使用中工作區。 選取藍色箭頭可設定使用中的工作區。 每個工作區右邊的設定 (齒輪) 圖示可讓您變更其名稱、位置和命令列引數。 紅色 X 會移除以手動方式新增的工作區。

本主題內容：

- [儲存並重設工作區](#saving-and-resetting-a-workspace)
- [本機工作區](#local-workspaces)
- [遠端工作區](#remote-workspaces)
- [切換工作區](#switching-between-workspaces)
- [本機和遠端電腦上的目錄](#directories-on-local-and-remote-computers)
- [將專案檔案複製到遠端工作區](#copying-project-files-to-remote-workspaces)
- [從遠端工作區複製檔案](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>儲存並重設工作區

根據預設，當您關閉並重新開啟專案時，RTVS 不會儲存工作區狀態。 但是您可以透過[工作區選項](options.md#workspace)變更此行為。

[R 工具] > [工作階段] > [重設] 命令以及互動視窗中的重設工具列按鈕，也會隨時重設工作區狀態。 如為遠端工作區，重設的效果是刪除第一次連線到遠端伺服器時所建立的使用者設定檔，這其實會刪除此處累積的任何檔案。

## <a name="local-workspaces"></a>本機工作區

[本機工作區] 清單會顯示您電腦上安裝的所有 R 解譯器。 

RTVS 嘗試在 Visual Studio 啟動時，透過查看 `HKEY_LOCAL_MACHINE\Software\R-Core\` 中的登錄機碼，自動偵測您已安裝的所有 R 版本。 因為這項檢查只會在啟動時完成，所以如果您安裝了新的 R 解譯器，就需要重新啟動 Visual Studio。

RTVS 可能偵測不到非以標準方式安裝的 R 解譯器 (例如，僅將檔案複製到資料夾而不是執行安裝程式)。 如果是這種情況，請以手動方式建立新的本機 R 工作區，如下所示︰

1. 選取 [工作區] 視窗中的 [新增] 按鈕。
1. 輸入新工作區的名稱。
1. 輸入 R 根資料夾的路徑，亦即包含 `bin` 資料夾及解譯器的路徑，以及 RTVS 啟動時，傳遞至解譯器的任何選用命令列引數。
1. 完成後選取 [儲存]。

![新增新的工作區](~/docs/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>遠端工作區

遠端工作區可讓您連線到遠端電腦的 R 工作階段。 (如需如何設定此用途的電腦，請參閱[設定遠端工作區](workspaces-remote-setup.md)。)

RTVS 不會自動偵測遠端工作區，所以您必須使用 [工作區] 視窗中的 [新增] 按鈕，手動新增它們，如上一節中所述。 在此情況下，請輸入遠端電腦的 URI，而不是輸入本機路徑。

> [!Important]
> 遠端工作區是由「必須使用 HTTPS 通訊協定」的 URI 所識別，以確保與遠端電腦通訊的隱私權和完整性。 RTVS 不會連線到不支援 HTTPS 的遠端電腦。

> [!Note]
> 遠端工作區預覽有效。 我們正在努力改善未來版本的檔案同步實作問題，歡迎您提供想法和意見反應，讓我們為您提供更好的體驗。


## <a name="switching-between-workspaces"></a>切換工作區

RTVS 一次僅繫結至一個工作區，這會由 [工作區] 視窗中該工作區的小型綠色核取記號表示。 根據預設，RTVS 會繫結至您在上一個工作階段中開啟的最後一個本機工作區。

若要變更使用中的工作區，請選取所需工作區旁的藍色箭號。 如此一來，系統會提示您儲存工作階段、終止目前的工作區，然後切換到新的工作區。

> [!Tip]
> 若要停用儲存提示，請選取 [R 工具] > [選項] 命令，並將 [在切換工作區前顯示確認對話方塊] 選項設為 `No`。 請參閱[工作區選項](options.md#workspace)。

如果您嘗試切換至已解除安裝的本機工作區或無法使用的遠端工作區，您可能會遇到 RTVS 專案未繫結至任何工作區的情況。 結果，當您在互動視窗中輸入程式碼，或另行嘗試執行程式碼時，可能會看到類似下面的錯誤。 若要修正此問題，只要切換到 [工作區] 視窗中的另一個工作區即可。 如果沒有任何可用的工作區，您必須安裝 R 解譯器。 您也可以嘗試在 Visual Studio 執行時，重新啟動已安裝解譯器的 Visual Studio。

![沒有任何工作區繫結至 RTVS 時發生錯誤](~/docs/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>切換至遠端工作區

RTVS 會在您第一次連線到遠端工作區時提示您輸入認證，然後 (使用安全的 Windows 認證保險箱) 快取這些認證供後續工作階段使用。 然後透過 HTTPS 安全地與遠端伺服器完成通訊 (這是必要的)。

根據伺服器的組態，您可能會在連線時看到憑證警告，「遠端 R 服務所顯示的安全性憑證不允許我們證明您已確實連線到電腦 (名稱)」。

![連線到遠端工作區時出現自我簽署憑證警告](~/docs/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

憑證是您嘗試要連接的電腦向 RTVS 提出的一份文件，其包含一個欄位可識別該機器的 URI。 當 RTVS 偵測到憑證中的 URI 與連接電腦所用的 URI 不符時，就會發出警告，指出伺服器的安全性可能已遭入侵。

不過，如果遠端電腦使用「自我簽署憑證」來啟用 HTTPS，而不是使用信任的提供者憑證，也會出現這項警告。 如需詳細資料，請參閱[設定遠端工作區](workspaces-remote-setup.md)。

## <a name="directories-on-local-and-remote-computers"></a>本機和遠端電腦上的目錄

根據預設，當您在本機工作區中啟動新的 R 解譯器時，目前的工作目錄會是 `%userprofile%\Documents`。 您可以使用 [R 工具] > [工作目錄] 命令隨時變更此項目，或以滑鼠右鍵按一下 Visual Studio 方案總管中的專案，然後選取 [在這裡設定工作目錄] 等命令。

在遠端電腦上，當您第一次連接到該伺服器時，RTVS 會根據您的認證自動建立使用者設定檔，所以工作目錄是該設定檔下的 `Documents` 資料夾。 這會用於所有使用相同認證的後續遠端工作階段。 

如此一來，程式碼實際執行的位置在本機和遠端工作區就不同。 然後，在您的程式碼中避免使用資料檔案等的絕對路徑，因為您的程式碼不可能帶到其他工作區。 請改用相對路徑。

亦請注意，在遠端工作區中，各個工作階段工作目錄中的所有檔案仍都保留在相同使用者設定檔原位。 如前所述，您可以在使用遠端工作區時，使用 [R 工具] > [工作階段] > [重設] 命令 (或互動視窗中的 [重設] 按鈕) 刪除這些項目。 這會再次刪除伺服器中的使用者設定檔，當您重新連線時會重新建立。

## <a name="copying-project-files-to-remote-workspaces"></a>將專案檔案複製到遠端工作區

在 Visual Studio 中使用 R 專案時，即使您使用遠端工作區，本機電腦一律有最新的專案檔案。 亦即當您在 Visual Studio 中開啟專案時 (通常表示開啟包含該專案的解決方案)，RTVS 會假設專案的內容完全位於本機電腦上。 遠端工作區其實只是專案檔案和任何程式碼輸出的暫存主機。 這表示，例如當使用互動視窗的 `source` 載入檔案時，該檔案必須已在您提供的遠端電腦路徑中，或者必須在遠端 R 解譯器目前的工作目錄中 (以 `setwd()` 函式設定)。

檔案會複製到遠端伺服器，如下所示︰

- 若要透過互動視窗從遠端使用檔案，您必須先在方案總管中以滑鼠右鍵按一下這些檔案 (或專案)，然後選取 [Source Selected] (選取的來源) 來手動複製這些檔案。 個別檔案會複製到伺服器的工作目錄。複製專案時，RTVS 會建立專案的資料夾。

- 您也可以在方案總管中選取檔案，然後選取 [所選來源檔案] 來複製檔案。 這會將它們載入互動視窗，並在此執行。 如果工作階段連線到遠端電腦，檔案會先複製至該處。

- 當 RTVS 繫結至遠端工作區而您按 F5 鍵時，選取 [偵錯] > [啟動偵錯] 或另行開始執行您的程式碼，RTVS 預設會自動將專案檔案複製到遠端工作區 (如需控制方法請參閱下文)。

- 會覆寫伺服器上原有的任何檔案。

> [!Note]
> 因為 RTVS 無法可靠攔截所有的 R 函式呼叫，所以來自互動視窗的 `source()` 或 `runApp()` 等呼叫函式 (適用於 Shiny 應用程式)「不會」將檔案複製至遠端工作區。

無論檔案執行時 RTVS 是否複製檔案，且實際複製的檔案為何，都是透過[專案屬性](projects.md#project-properties)控制。 若要開啟此頁面，請選取 [專案] > [(name) Properties...] ((名稱) 屬性...) 功能表命令，或以滑鼠右鍵按一下方案總管中的專案，然後選取 [屬性...]。

![專案屬性執行索引標籤與檔案傳輸設定](~/docs/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

在此，[Transfer files on run] (執行時傳輸檔案) 會判斷 RTVS 是否自動複製專案檔案。 接著 [Files to transfer] (要傳輸的檔案) 值會確實篩選要傳送哪些檔案。 預設值為僅複製 `.R`、`.Rmd`, `.sql`、`.md` 和 `.cpp` 檔案。 這是為了避免每次執行時不小心將大型的資料檔案複製到伺服器。 

## <a name="copying-files-from-a-remote-workspace"></a>從遠端工作區複製檔案

如果您的 R 指令碼會在伺服器上產生檔案，您可以使用 `rtvs::fetch_file` 函式將這些檔案複製回用戶端。 此函式至少會接受您想要複製到電腦的檔案遠端路徑，或者您想要複製該檔案的目標電腦路徑。 如果您不指定路徑，檔案就會複製到您的 `%userprofile%\Downloads` 資料夾。

