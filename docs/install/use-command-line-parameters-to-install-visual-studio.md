---
title: "使用命令列參數安裝 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>使用命令列參數安裝 Visual Studio 2017 RC
當您從命令提示字元安裝 Visual Studio 2017 RC 時，您可以使用下列命令列參數 (parameter) (也稱為參數 (switch))。  

## <a name="list-of-command-line-parameters"></a>命令列參數清單  
 Visual Studio 命令列參數不區分大小寫。  

| **命令列命令** | **說明** |
| ----------------------- | --------------- |  
| ```modify``` | 修改所安裝的產品。 |
| ```update``` | 更新所安裝的產品。 |
| ```repair``` | 修復所安裝的產品。 |
| ```uninstall``` | 解除安裝所安裝的產品。 |

如果未指定任何命令，則會安裝產品。

| **命令列選項** | **說明** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | 要操作之執行個體的安裝目錄。 若是安裝命令，這是執行個體的安裝位置。 若是其他命令，這是先前安裝之執行個體的安裝位置。 |
| ```--productId <id>``` | 要安裝之執行個體的產品識別碼。 這對安裝命令是必要的，對其他指定了 --installPath 的命令則會予以略過。 |
| ```--layout <dir>``` | 選擇性︰指定一個目錄以建立離線安裝快取。 選取此選項也會以隱含方式新增 '--wait' 選項。 |
| ```--lang <language-locale>``` *[&#60;語言地區設定&#62; ...]* | 選擇性︰安裝/解除安裝指定語言的資源套件。 |
| ```--add <workload or component ID>``` *[&#60;工作負載或元件識別碼&#62; ...]* | 選擇性︰要新增的一或多個工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 '--includeRecommended' 及 (或) '--includeOptional' 全域控制其他元件。 如需更精細的控制，您可以將 ';includeRecommended' 及 (或) ';includeOptional' 附加至 artifactId (例如 '--add Workload1;includeRecommended' 或 '--add Workload2;includeOptional;includeRecommended')。 |
| ```--remove <workload or component ID>``` *[&#60;工作負載或元件識別碼&#62; ...]* | 選擇性︰要移除的一或多個工作負載或元件識別碼。 |
| ```--all``` | 選擇性︰是否要安裝產品的所有工作負載和元件。 |
| ```--allWorkloads``` | 選擇性︰安裝所有工作負載及其必要元件，但不安裝建議或選用元件。 |
| ```--includeRecommended``` | 選擇性︰包含所安裝之任何工作負載的建議元件，但不包含選用元件。 使用 --allWorkloads 或 --add 指定工作負載。 |
| ```--includeOptional``` | 選擇性︰包含所安裝之任何工作負載的選用元件，但不包含建議元件。 使用 --allWorkloads 或 --add 指定工作負載。  |
| ```--quiet, -q``` | 選擇性︰執行安裝時不顯示任何使用者介面。 |
| ```--passive, -p``` | 選擇性︰顯示使用者介面，但不會向使用者要求任何互動。 |
| ```--norestart``` | 選擇性︰如果存在，搭配 --passive 或 --quiet 的命令將不會自動重新啟動電腦 (如有必要)。 如果未指定 --passive 或 --quiet，則會略過此選項。  |
| ```--locale <language-locale>``` | 選擇性︰變更安裝程式之使用者介面的顯示語言。 設定將會予以保留。 |
| ```--nickname <name>``` | 選擇性︰這會定義要指派給所安裝產品的暱稱。 暱稱的長度不能大於 10 個字元。  |
| ```--help, --?, -h, -?``` | 顯示參數使用方式。 |

>注意︰指定多個工作負載和元件時，您必須針對每個項目重複 `--add` 或 `--remove` 命令列參數。

| **進階命令列選項** | **說明** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | 選擇性：要安裝之執行個體的通道識別碼。 這對安裝命令是必要的，對其他指定了 --installPath 的命令則會予以略過。 |
| ```--channelUri <uri>``` | 選擇性︰通道資訊清單的 URI。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| ```--installChannelUri <uri>``` | 選擇性︰要用於安裝之通道資訊清單的 URI。 以 --channelUri 指定的 URI (指定 --installChannelUri 時必須指定) 將用來偵測更新。 如果不需要更新，就必須指定未提供引數的 --channelUri。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| ```--installCatalogUri <uri>``` | 選擇性︰要用於安裝之目錄資訊清單的 URI。 如果指定，通道管理員會嘗試從此 URI 下載目錄資訊清單，再於安裝通道資訊清單中使用此 URI。 此參數可用來支援離線安裝，在此安裝中會使用已下載的產品目錄來建立配置快取。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| ```--in <path>``` | 選擇性︰回應檔的 URI 或路徑。  |
| ```--addProductLang <language-locale>``` | 選擇性︰這會定義所要安裝之成品 (群組、工作負載或元件) 的語言。 它可在命令列上出現多次。 它對安裝和修改命令是選擇性的，對更新、修復和解除安裝命令則會予以略過。 如果不存在，安裝將會使用電腦地區設定。 |
| ```--removeProductLang <language-locale>``` | 選擇性︰這會定義所要移除之成品 (群組、工作負載或元件) 的語言。 它可在命令列上出現多次。 它對安裝和修改命令是選擇性的，對更新、修復和解除安裝命令則會予以略過。 |
| ```--wait``` | 選擇性︰處理序會等候安裝完成，再傳回結束代碼。 這適用於自動化安裝的情況，在此情況下，使用者必須等候安裝完成，才能處理該安裝的傳回碼。 |
| ```--productKey``` | 選擇性︰這會定義要用於所安裝產品的產品金鑰。 它是由 25 個英數字元組成，格式為 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' 或 'xxxxxxxxxxxxxxxxxxxxxxxxx'。 |
## <a name="list-of-workload-ids-and-component-ids"></a>工作負載識別碼和元件識別碼清單
如需依 Visual Studio 產品排序的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (Visual Studio 2017 工作負載和元件識別碼) 頁面。

> [!WARNING]
> 如果 setup .exe 檔案名稱包含數字，--layout 參數將會失敗。 若要解決此問題，您必須將檔名的數字移除&mdash;例如，將 *vs_community__198521760.1486960229.exe* 重新命名為 ***vs_community.exe***。

## <a name="list-of-language-locales"></a>語言地區設定清單
| **語言地區設定** | **語言** |
| ----------------------- | --------------- |  
| cs-CZ | 捷克文 |
| de-DE | 德文 |
| zh-TW | 英文 |
| es-ES | 西班牙文 |
| cs-CZ | 捷克文 |
| fr-FR | 法文 |
| it-IT | 義大利文 |
| ja-JP | 日文 |
| ko-KR | 韓文 |
| pl-PL | 波蘭文 |
| pt-BR | 葡萄牙文 - 巴西 |
| ru-RU | 俄文 |
| tr-TR | 土耳其文 |
| zh-CN | 簡體中文 |
| zh-TW | 繁體中文 |



> [!IMPORTANT]
> 雖然 Visual Studio 2017 RC 一般支援在生產環境中使用，但安裝 UI 中標示為「預覽」的這些工作負載和元件不支援在生產環境中使用。

## <a name="see-also"></a>請參閱

 * [安裝 Visual Studio](install-visual-studio.md)
 * [建立 Visual Studio 2017 RC 的離線安裝](create-an-offline-installation-of-visual-studio.md)
 * [回報在使用 Visual Studio 時發生的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

