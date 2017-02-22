---
title: "Guid 和 Id 的 Visual Studio 工具列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visual studio 群組"
  - "工具列"
  - "visual studio 工具列"
  - "id"
  - "toolgar 群組"
  - "工具視窗工具列"
  - "guid"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Guid 和 Id 的 Visual Studio 工具列
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本節列舉的 GUID 及識別碼值 Visual Studio 的整合式的開發環境 \(IDE\) 中所包含的工具列，而且在它們包含的群組。  這些值會定義在.vsct 所安裝檔案做為 Visual Studio 的 SDK 的一部分。  如需詳細資訊，請參閱 [IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
> [!NOTE]
>  許多可用的工具列 Visual Studio 至未定義的 Visual Studio，以及它們的 GUID 及識別碼值不是公用。  本主題列出 Visual Studio SDK.vsct 檔案中定義的工具列。  
  
 如需有關如何使用.vsct 檔案中定義的 IDE 物件的詳細資訊，請參閱[擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 Visual Studio 的 IDE 所提供的預設工具列使用 GUID `guidSHLMainMenu`，否則使用 GUID:ID 語法來指定除外。  
  
## IDE 工具列  
 下列的工具列所提供的 Visual Studio 的 IDE 中。  可以顯示工具列，請選取圖形上**工具列** \] 子功能表的 **工具**功能表。  本章節中不包括的工具視窗的工具列。  
  
 只有群組\]，可以直接從工具列下降。  若要新增的群組，請設定其父代的 GUID 及識別碼的工具列。  新增按鈕到工具列，請設定群組\] 工具列上的與其父代。  
  
|Toolbar|ID|  
|-------------|--------|  
|Standard 版|IDM\_VS\_TOOL\_STANDARD|  
|建置|IDM\_VS\_TOOL\_BUILD|  
|文字編輯器|IDM\_VS\_TOOL\_TEXTEDITOR|  
|偵錯|guidVSDebugGroup:IDM\_DEBUG\_TOOLBAR|  
|偵錯位置|guidVSDebugGroup:IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### 特殊的工具列  
 這些工具列所定義的 Visual Studio 的 IDE 中，但提供特殊的函式並不主控命令群組。  
  
|Toolbar|ID|  
|-------------|--------|  
|新增指令|IDM\_VS\_TOOL\_ADDCOMMAND|  
|未定義|IDM\_VS\_TOOL\_UNDEFINED|  
|XML 結構描述|IDM\_VS\_TOOL\_SCHEMA|  
|XML 資料|IDM\_VS\_TOOL\_DATA|  
  
## 在 IDE 工具列上的群組  
 若要新增到 \[標準\] 工具列的按鈕，設定下列群組的其中一個做為其父系。  群組被按照父工具列。  
  
### 標準工具列群組  
  
|名稱|ID|  
|--------|--------|  
|儲存或開啟|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|剪下\/複製|IDG\_VS\_TOOLSB\_CUTCOPY|  
|復原\/取消復原|IDG\_VS\_TOOLSB\_UNDOREDO|  
|執行\/建築|IDG\_VS\_TOOLSB\_RUNBUILD|  
|搜尋|IDG\_VS\_TOOLSB\_SEARCH|  
|視窗|IDG\_VS\_TOOLSB\_WINDOWS|  
|新視窗|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|載入\/儲存|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|彩色儀表|IDG\_VS\_TOOLSB\_GAUGE|  
  
### 建立工具列群組  
  
|名稱|ID|  
|--------|--------|  
|組建列|IDG\_VS\_BUILDBAR|  
|Cancel|IDG\_VS\_BUILD\_CANCEL|  
  
### 文字編輯器\] 工具列上的群組  
  
|名稱|ID|  
|--------|--------|  
|完成|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Indent|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|註解|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|書籤|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### 偵錯\] 工具列的群組  
  
|名稱|ID|  
|--------|--------|  
|執行|IDM\_DEBUG\_TOOLBAR|  
|逐步執行|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|視窗|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### 偵錯位置工具列群組  
  
|名稱|ID|  
|--------|--------|  
|偵錯位置|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## 工具視窗工具列  
 工具列可以直接在 IDE 中或出現在工具視窗如**方案總管\] 中**。  工具視窗未定義在.vsct 檔案，因為工具視窗工具列中沒有已定義的父代。  相反地，它們會放在程式碼中。  下表顯示的工具列會出現在工具視窗在 IDE 中，以及它們所包含的命令群組。  
  
> [!NOTE]
>  工具列和群組使用 GUID `guidSHLMainMenu`，否則使用 GUID:ID 語法來指定除外。  在工具列指定一個 GUID，它也適用於該工具列從下降的群組。  
  
|工具視窗|Toolbar|Group|  
|----------|-------------|-----------|  
|方案總管|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1。.5|  
|伺服器總管|guid\_SE\_MenuGroup:IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|屬性|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|類別檢視|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|類別檢視|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEARCH2|  
|物件瀏覽器|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|物件瀏覽器|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEARCH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|尋找和取代|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|尋找結果 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|尋找結果 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|書籤|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|工作清單|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|使用者工作|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|錯誤清單|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|呼叫瀏覽器|IDM\_VS\_TOOL\_CALLBROWSER1。.16|IDG\_VS\_TOOLBAR\_CALLBROWSER1\_ACTIONS<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_TYPE<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_CBSETTINGS|  
|中斷點|guidVSDebugGroup:IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|反組譯碼|guidVSDebugGroup:IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|1\-4 的記憶體|guidVSDebugGroup:IDM\_MEMORY\_WINDOW\_TOOLBAR1…4|IDG\_MEMORY\_EXPRESSION1。.4<br /><br /> IDG\_MEMORY\_COLUMNS1。.4|  
|處理序|guidVSDebugGroup:IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXECCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## 請參閱  
 [加入至工具列功能表控制器](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [將工具列新增至工具視窗](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Guid 和 Id 的 Visual Studio 功能表](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)