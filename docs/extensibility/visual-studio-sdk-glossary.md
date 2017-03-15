---
title: "Visual Studio SDK 詞彙 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "字彙 [Visual Studio SDK]"
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Visual Studio SDK 詞彙
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

僅提供所用的詞彙定義 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 文件。  
  
## 詞彙  
 增益集  
 公用程式的應用程式、 驅動程式或其他軟體新增至主應用程式。 在 Visual Studio 整合式的開發環境 \(IDE\) 中，增益集是自動化架構的應用程式擴充功能的 IDE。  
  
 automation 模型  
 Automation 模型，在舊版的 Visual Studio 擴充性模型，以得知是程式設計介面，可讓您存取下面的常式該磁碟機的 IDE。 增益集、 精靈和巨集使用中控制項的 automation 模型的物件或擴充功能的 IDE。  
  
 命令 UI 的內容  
 關聯的 GUID 與 UI 命令或工具列等項目的可見性。 命令 UI 的內容會與選取範圍內容不同，因為它並未附加至視窗。  
  
 可用於命令 UI 內容:  
  
-   將 GUID 指派給特定的視窗啟動時出現的工具列。  
  
-   要將 GUID 指派給命令的可用性，而不必載入或執行 VSPackage。  
  
-   指定會影響使用中的索引鍵繫結的 GUID。  
  
-   指定開啟錄製巨集的 GUID。  
  
-   指派的 GUID，若要啟動偵錯模式或設計並在編輯器中的執行的模式之間切換。  
  
 元件  
 可以透過組件的應用程式的功能不需要具有預先存在的任何資訊的軟體實作該應用程式的軟體的部分。 元件和應用程式之間的通訊是完全透過 OLE 樣式的介面。  
  
 元件管理員  
 服務， `SOleComponentManager`, ，它會提供最上層元件的非使用者介面協調服務。`SOleComponentManager` 服務會實作 `IOleComponentManager` 介面。  
  
 元件 UI 管理員  
 服務， `SOleComponentUIManager`, ，它會提供使用者介面協調服務。`SOleComponentUIManager` 服務會實作 `IOleComponentUIManager` 和 `IOleInPlaceComponentUIManager` 介面。  
  
 內容包  
 `IVsUserContext` 物件 \(COM 物件\) 附加至環境元件。 此物件會保存查詢關鍵字、 F1 關鍵字和相關元件的屬性。 此外，內容包點來連結至其任何子內容包。  
  
 內容提供者  
 IDE 具有與其相關聯的內容封包中的元件。 這類元件包括工具視窗、 編輯器或專案階層架構。  
  
 設計工具  
 程式設計介面，可讓使用者管理 UI \(表單、 按鈕和其他控制項\) 的項目。  
  
 DocData  
 封裝的世界中的文件的基礎資料的 COM 物件的文件\/檢視的分隔 \(例如，在文字編輯器的情況下，這會是基礎所有的文字編輯器檢視文字緩衝區\)。 如果 EditorFactory 未提供此物件，IDE 會製造一個代表它執行動作。 此物件負責管理資料持續性和多個共用語意 \(semantics\) 會透過檢視此相同 `DocData`。 如果 `DocData` 物件支援 `IOleCommandTarget` 介面，將會納入 UIShell 的命令路由。  
  
 DocObject  
 用來裝載主機提供的範圍內的 UI 的技術。 更具體來說，此術語是指支援任何內嵌 `IOleDocument` 和相關的介面。 這項技術有許多潛在的應用程式，例如 COM 文件的實作詳細資料，在 Visual Basic 5.0 中的工具視窗時，ActiveX 設計工具在 Visual Basic 6.0 中，以此類推。  
  
 文件  
 用來參考以一般方式整個文件，同時 `DocData` 和 `DocView`。 例如，包含 DocumentFrame `DocView`, ，但它也會保留參考 `DocData` 處理持續性。  
  
 DocView  
 DocObject\/內嵌\/視窗窗格與使用者互動來檢視和管理基礎 `DocData`。 請注意，使用者並不會屬於文件\/檢視分隔的優點 `DocObject` 介面設計。 使用者用來做為檢視，而不是使用更抽象的 \(和較不正式\) 的概念為基礎的資料的整個 DocObject `DocData`。`DocView` 物件永遠會內嵌在 ide 的文件框架物件 \(MDI 子視窗\)。  
  
 DTE  
 `DTE` \(開發工具擴充性\) 的物件是在 Visual Studio automation 模型，可讓您以程式設計方式自動化和擴充 IDE 的最高的存取點。  
  
 動態說明\] 視窗  
 工具視窗，IDE 會實作，而且會顯示一份查閱關鍵字或 F1 說明主題。  
  
 編輯器  
 實作的程式碼 \(類別、 CLSID\) `DocView`。 它也會實作 `DocData` 支援檢視\/資料分離，則為。  
  
 擴充功能  
 此功能可修改、 自訂，或新增至 IDE。 您建立使用 automation 模型或 Vspackage 擴充功能。  
  
 外部編輯器  
 編輯器不是專用的 ide，例如 Microsoft Word。 它已登錄它自己的機制，並可在 IDE 之外。 這個編輯器可內嵌，會出現在 IDE 中的視窗內。 如果無法內嵌，則會建立個別的最上層視窗。  
  
 階層  
 節點的樹狀結構，每個節點相關聯的一組屬性。  
  
 獨立的最上層元件  
 元件會使用非強制回應的最上層視窗及可作為獨立的應用程式視窗中，有效地運作，但會實作為同處理序物件。 因此，最上層的獨立元件必須協調模式和訊息迴圈服務和 IDE。 同處理序物件沒有自己的訊息迴圈。  
  
 資訊提供者  
 資訊提供者是一個模組，可以查閱關鍵字，並傳回的主題清單的形式 `IVsUserContextItem` 物件。 若要提供 F1 和查詢關鍵字項目資訊提供者，註冊編譯的說明檔 \(。HxS\) 與系統。 這些檔案中的 \[說明\] 主題可提供的動態說明\] 視窗中顯示，並顯示使用者是否按下 F1 的主題清單。  
  
 就地元件  
 實作的 VSPackage 物件 `IOleInPlaceComponent` 介面來管理以視覺化方式包含在 IDE 所擁有的文件視窗的視窗。 就地元件不會參與標準 OLE 功能表合併。而是它們會將其使用者介面項目整合到 IDE。  
  
 有兩種就地元件類型: 硬式編碼在就地元件和控制項的元件。  
  
 硬式編碼在就地元件有功能表、 工具列和緊密整合到 IDE 中顯示為如果它們已直接內建 IDE 的使用者介面的命令。  
  
 元件控制項不具有任何整合到 IDE; 其本身使用者介面項目而是使用 IDE 的功能表、 命令和工具列。 比方說，粗體顯示的命令可用來以粗體顯示在表單中內嵌的 rtf 文字控制項中選取的文字。 不過，元件控制項可以要求會以動態方式安裝的特定元件的 UI 項目。  
  
 語言服務  
 一組物件可供 VSPackage 開發人員實作功能的電腦語言程式碼編輯器，例如文字標記與上色功能。  
  
 其他檔案專案  
 用來存放不在任何專案中的開啟檔案的專案。 不會保存此專案中的項目清單。  
  
 專案  
 專案由階層物件所組成，則 COM 物件實作 `IVsHierarchy` 介面。  
  
 特定專案設計工具或編輯器  
 此設計工具無法使用獨立於專案類型。 所有特定專案設計工具必須在登錄中都輸入其編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具只要在特定專案中開啟特定檔案類型。  
  
 專案類型\] 視窗  
 持續追蹤目前作用中的專案階層架構和項目，從全域範圍內容視窗。 使用 \[專案類型 windows `SVsTrackSelectionEx` 服務警示變更的 IDE，並向使用者顯示意見反應。 方案總管\] 是 \[專案類型\] 視窗的範例。  
  
 屬性視窗  
 先前屬性瀏覽器。  
  
 參考為基礎的專案  
 不需要是相同的目錄中之專案檔案的專案。 相反地，從其他不相關的目錄檔案的參考儲存和維護專案本身。  
  
 執行中的文件表格  
 內部結構，IDE 會維護所有目前開啟的文件的清單。 這份清單包含所有開啟的文件，不論是否目前正在編輯文件的記憶體中。 文件是儲存，包括開啟編輯器、 專案中的檔案或主要專案檔 \(例如，\*.vcproj 檔案\) 中的預存程序的任何項目。  
  
 選取項目內容  
 資料是在 IDE 中的每個視窗的詳細資料的一部分，用來追蹤使用中的選取項目。 選取範圍內容所組成:  
  
-   指標 `IVsHierarchy` 介面的專案階層架構  
  
-   專案項目的項目識別項。  
  
-   指標 `ISelectionContainer` 提供存取的作用中的物件屬性的介面。  
  
-   項目值的陣列。  
  
 服務  
 一組 COM 介面的單一 COM 物件中的合約。 當您建立的服務，由 GUID 識別，您會定義都包含在內服務 COM 介面的集合。 COM 物件會使用服務來與彼此通訊。  
  
 方案  
 群組中的使用者使用與其相關的專案。  
  
 標準的設計工具  
 設計工具可用來與專案類型無關。 所有標準的設計工具必須在登錄中輸入其編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具時開啟特定副檔名的檔案。 資料必須保存至檔案。  
  
 標準編輯器  
 可以使用獨立於任何特定專案類型的編輯器。 這類編輯器有 EditorFactories 在登錄中。 這可讓 IDE 找出並叫用編輯器。  
  
 標準的 OS 編輯器  
 內嵌不是 Visual Studio 特定。 註冊使用已知的 Win32 索引鍵 \(例如，Win32 總管知道如何叫用\)。 如果這類編輯器可以內嵌，編輯器仍出現在其位置在 IDE 中。 否則，會建立個別的最上層視窗，這類的編輯器。  
  
 子內容包  
 `IVsUserContext` 物件連結到的內容封包。 此物件會保存查詢關鍵字、 F1 關鍵字和 IDE 元件中的選取範圍的屬性。 子內容的範例包括命令中工具視窗或在編輯器中的關鍵字。  
  
 工作清單  
 工具視窗，IDE 會實作，而且會顯示作用中工作的清單。  
  
 文字緩衝區  
 物件的一般名稱 `VSTextBuffer`。  
  
 文字檢視  
 物件的一般名稱 `VSTextView`。  
  
 工具的最上層元件  
 設備的非強制回應快顯視窗，緊密協調與 IDE 的使用者介面元件。 獨立的最上層元件，例如模式和訊息迴圈服務與 IDE，也必須協調工具最上層元件。  
  
 最上層的元件  
 管理非強制回應的最上層視窗，而不是 IDE 視窗的工作區 VSPackage 物件。 最上層元件會實作 `IOleComponent` 介面，以利用訊息迴圈服務，例如存取閒置的時間。  
  
 使用中的 UI  
 VSPackage 物件，可以看到，且目前具有焦點。  
  
 UI 階層架構  
 COM 物件實作 `IVsUIHierarchy` 介面，讓階層的顯示。 實作 UI 階層架構視窗 `ISelectionContainer` 介面來更新 \[屬性\] 視窗; 其他專案類型 windows 才能使用此實作中，如有需要。  
  
 VSCT  
 Visual Studio 命令的資料表。 .Vsct 檔包含資訊的位置和功能表、 工具列和命令，以 XML 格式的行為。  
  
 VSPackage  
 藉由參與一或多個項目延伸 Visual Studio IDE 的軟體可安裝部分: 使用者介面、 服務、 專案類型或編輯器\/設計工具。 VSPackage 包含實作的 COM 物件 `IVsPackage` 介面以及一個或多個其他 COM 物件實作其他介面，以支援選取範圍和其他功能。 此外，VSPackage 有特定的註冊需求。