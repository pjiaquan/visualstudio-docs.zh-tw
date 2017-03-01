---
title: "設計 XML 命令資料表 (。Vsct) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>設計 XML 命令資料表 (。Vsct) 檔案
XML 命令資料表 (.vsct) 檔案會描述 VSPackage 命令項目的外觀與配置。 命令的項目包括按鈕、 下拉式方塊、 功能表、 工具列和命令的項目群組。 本主題描述 XML 命令資料表檔案、 它們如何影響命令項目和功能表，以及如何建立它們。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>命令、 功能表、 群組和.vsct 檔案  
 .vsct 檔案被按照命令、 功能表和命令群組。 .Vsct 檔中的 XML 標記代表每一個項目，以及其他相關的項目，例如命令按鈕、 命令位置與點陣圖。  
  
 當您建立新的 VSPackage 執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]套件 範本，範本會產生必要的項目.vsct 檔案功能表命令、 工具視窗中，或自訂編輯器，視您的選擇而定。 這個.vsct 檔案便可加以修改以符合特定 VSPackage 的需求。 如需如何修改.vsct 檔的範例，請參閱中的範例[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 若要建立新的空白.vsct 檔，請參閱[How to︰ 建立。Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)。 一旦建立之後，您加入 XML 項目、 屬性和值來描述命令項目配置的檔案。 詳細的 XML 結構描述，請參閱[VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc 和.vsct 檔案之間的差異  
 雖然為那些在現在已被取代.ctc 檔案格式中.vsct 檔的 XML 標記背後的意義都是相同的其實是有點不同。  
  
-   新** \<extern >**標記是您用來參考其他的.h 檔案進行編譯，例如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]工具列。  
  
-   而.vsct 檔案支援**/ 包括**陳述式，.ctc 檔案一樣，它也提供了新\<**匯入 >**項目。 其差別是， **/ 包括**帶入**所有**的資訊，但\<**匯入 >**帶入只有名稱。  
  
-   雖然.ctc 檔案需要您在其中定義在前置處理器指示詞的標頭檔，其中一個不需要.vsct 檔案。 相反地，將在指示詞放在符號表中，位於**\<符號 >**項目，位於底部的.vsct 檔。  
  
-   .vsct 檔案功能**\<註解 >**標記，可讓您內嵌，例如註解或甚至是圖片的任何資訊。  
  
-   值會儲存為項目上的屬性。  
  
-   命令旗標可以儲存在個別或堆疊。  Intellisense，不過，無法運作的堆疊的命令旗標。 如需命令旗標的詳細資訊，請參閱[命令旗標的項目](../../extensibility/command-flag-element.md)。  
  
-   您可以指定多個類型，例如分割下拉式清單、 組合等等。  
  
-   未經驗證的 Guid。  
  
-   每個 UI 項目具有與它所顯示的文字表示的字串。  
  
-   父代是選擇性的。 如果省略，則會使用 「 群組不明 」 的值。  
  
-   圖示引數是選擇性的。  
  
-   檔案 [點陣圖] 區段-.ctc 相同，不同之處在於您現在可以指定檔案名稱，透過提取它會 vsct.exe 編譯器在編譯時期的 href。  
  
-   ResID-舊的點陣圖資源識別碼可用，而且仍然可以使用.ctc 檔案相同。  
  
-   HRef-新的方法，可讓您指定點陣圖資源的檔案名稱。 它會假設所有的使用，因此您可以略過 [使用] 區段。 編譯器會先搜尋本機資源的檔案，然後在任何網路共用資料夾，並且/I 參數所定義的任何資源。  
  
-   您不再需要 Keybinding-指定模擬器。 如果您指定其中一個，編譯器會假設編輯器和模擬器都相同。  
  
-   已經卸除 Keychord。 新的格式是 Key1、 Mod1、 Key2、 Mod2。  您可以指定字元、 十六進位、 或 VK 常數。  
  
 新編譯器、 vsct.exe，編譯.ctc 和.vsct 檔。 舊的 ctc.exe 編譯器，不過，將無法辨識也無法編譯.vsct 檔。  
  
 您可以使用 vsct.exe 編譯器將現有的.cto 檔轉換成.vsct 檔。 如需詳細資訊，請參閱[How to︰ 建立。從現有的 Vsct 檔案。Cto 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)。  
  
## <a name="the-vsct-file-elements"></a>.Vsct 檔項目  
 命令資料表具有下列階層和項目︰  
  
 [CommandTable 元素](../../extensibility/commandtable-element.md)— 表示所有的命令、 功能表群組和 VSPackage 相關聯的功能表。  
  
 [Extern 元素](../../extensibility/extern-element.md)— 參考任何您想要合併.vsct 檔的外部的.h 檔案。  
  
 [包含項目](../../extensibility/include-element.md)— 參考任何您想要編譯以及 your.vsct 檔案的其他標頭 (.h) 檔案。 .Vsct 檔可以包含.h 檔案，其中包含定義命令、 功能表群組和功能表提供 IDE 或另一個 VSPackage 的常數。  
  
 [命令元素](../../extensibility/commands-element.md)— 表示所有的個別可執行的命令。 每個命令會有下列四個子項目︰  
  
 [功能表項目](../../extensibility/menus-element.md)— 表示所有的功能表和工具列在 VSPackage 中的。 功能表是容器的命令群組。  
  
 [群組項目](../../extensibility/groups-element.md)— 代表所有在 VSPackage 中的群組。 群組為個別命令的集合。  
  
 [按鈕項目](../../extensibility/buttons-element.md)— 表示所有的命令按鈕和功能表項目在 VSPackage。 按鈕會與命令相關聯的視覺控制項。  
  
 [點陣圖的項目](../../extensibility/bitmaps-element.md)— 代表所有的 VSPackage 中的按鈕，所有的點陣圖。 點陣圖會顯示下一步或根據內容的 [命令] 按鈕的圖片。  
  
 [CommandPlacements 元素](../../extensibility/commandplacements-element.md)— 表示額外的位置，其中個別的命令應該要位於 VSPackage 的功能表。  
  
 [VisibilityConstraints 元素](../../extensibility/visibilityconstraints-element.md)-指定是否命令會顯示根本多次，或只在特定內容，例如特定的對話方塊或視窗會顯示。 功能表和命令的值，這個項目會顯示指定的內容是使用中時，才。 預設行為是一直顯示命令。  
  
 [按鍵組合的項目](../../extensibility/keybindings-element.md)— 指定命令的任何索引鍵繫結。 也就是說，一個或多個按鍵組合所必須執行的命令，例如按**CTRL + S**。  
  
 [UsedCommands 元素](../../extensibility/usedcommands-element.md)— Informs[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境雖然指定的命令由其他程式碼中，使用目前的 VSPackage 時，它會提供命令的實作。  
  
 `Symbols Element`-包含的符號名稱和所有您在封裝中的命令的 GUID 識別碼。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct 檔案設計指導方針  
 若要成功設計.vsct 檔，請遵循這些指導方針。  
  
-   命令可以放在群組中只、 群組只置於功能表和功能表可以放置只在群組中。 只有功能表會實際顯示在 IDE 中，群組和命令。  
  
-   子功能表不能直接指派給 功能表上，但必須指派給群組，依序指派給一個功能表。  
  
-   命令，讓子功能表和群組，都可以指派給一個父群組或使用其定義的指示詞的父欄位。  
  
-   組織僅透過指示詞中的父欄位的命令資料表有相當大的限制。 定義物件的指示詞可以採用只能有一個父引數。  
  
-   重複使用的命令、 群組或子功能表需要新的指示詞，以建立物件的新執行個體，其使用`GUID:ID`配對。  
  
-   每個`GUID:ID`組必須是唯一。 重複使用，例如放在功能表上，工具列上，或在內容功能表上的命令由<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   命令和子功能表也可以指派多個群組，並使用多個功能表指派給群組[Commands 元素](../../extensibility/commands-element.md)。  
  
## <a name="vsct-file-notes"></a>.Vsct 檔案資訊  
 如果.vsct 檔之後，您同時進行編譯，並且將它放在原生附屬 DLL 中進行任何變更，您應該執行**devenv.exe /setup /nosetupvstemplates**。 這樣會強制在實驗性的登錄，以可讀取和描述的內部資料庫中指定的 VSPackage 資源[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]重建。  
  
 在開發期間，可能會建立並登錄可能會導致在 IDE 中令人困惑的雜亂的實驗登錄區中的多個 VSPackage 專案。 若要修正此問題，您可以將實驗登錄區重設為預設設定，以移除所有已註冊的 VSPackages 和可能的 ide 所做的變更。 若要重設實驗登錄區，請使用隨附於 Visual Studio SDK CreateExpInstance.exe 工具。 您可以找到在  
  
 **%Programfiles (x86) %\Visual Studio\<版本 > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 使用命令列執行工具**CreateExpInstance /Reset**。 請記住，這項工具，移除實驗登錄區通常不會安裝所有已註冊的 VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)
