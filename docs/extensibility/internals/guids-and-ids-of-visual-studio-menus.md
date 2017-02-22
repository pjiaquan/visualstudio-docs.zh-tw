---
title: "Guid 和 Id 的 Visual Studio 功能表 | Microsoft Docs"
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
  - "visual studio 功能表"
  - "visual studio 群組"
  - "id"
  - "現有的功能表"
  - "guid"
  - "功能表"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Guid 和 Id 的 Visual Studio 功能表
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主題列舉功能表和 Visual Studio 功能表列上的群組的 GUID 和 ID 的值。 安裝過程中的 Visual Studio SDK 的.vsct 檔案中定義這些值。 如需詳細資訊，請參閱[IDE 定義的命令、 功能表和群組](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)。  
  
 如需如何使用.vsct 檔中所定義的整合式的開發環境 \(IDE\) 物件的詳細資訊，請參閱 [擴充的功能表和命令](../../extensibility/extending-menus-and-commands.md)。  
  
 功能表和 Visual Studio 功能表列上的群組使用的 GUID `guidSHLMainMenu`。 在功能表列本身的識別碼為 `IDM_VS_TOOL_MAINMENU`。  
  
## 在 Visual Studio 功能表列上的群組  
 若要加入功能表的功能表列，設定其中一個群組做為其父系。  
  
|群組|ID|  
|--------|--------|  
|檔案\/編輯檢視|IDG\_VS\_MM\_FILEEDITVIEW|  
|重構|IDG\_VS\_MM\_REFACTORING:|  
|專案|IDG\_VS\_MM\_PROJECT|  
|組建|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|格式\/工具|IDG\_VS\_MM\_TOOLSADDINS|  
|視窗\/說明\/社群|IDG\_VS\_MM\_WINDOWHELP|  
|增益集|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## 在 Visual Studio 功能表列上的功能表  
 若要新增群組至現有的 Visual Studio 功能表中，設定下列功能表的其中一個做為其父系。 這份清單中不包含子功能表。  
  
|功能表|ID|  
|---------|--------|  
|檔案|IDM\_VS\_MENU\_FILE|  
|Edit|IDM\_VS\_MENU\_EDIT|  
|檢視|IDM\_VS\_MENU\_VIEW|  
|重構|IDM\_VS\_MENU\_REFACTORING|  
|專案|IDM\_VS\_MENU\_PROJECT|  
|組建|IDM\_VS\_MENU\_BUILD|  
|格式|IDM\_VS\_MENU\_FORMAT|  
|工具|IDM\_VS\_MENU\_TOOLS|  
|視窗|IDM\_VS\_MENU\_WINDOW|  
|增益集|IDM\_VS\_MENU\_ADDINS|  
|社群|IDM\_VS\_MENU\_COMMUNITY|  
|說明|IDM\_VS\_MENU\_HELP|  
  
## 在 Visual Studio 功能表上的群組  
 以下清單顯示下降功能表直接從 Visual Studio 功能表列的群組。 將命令加入至 Visual Studio 功能表的最快速方式是其中一個群組設定為父代。 本章節中看不到來自子功能表的群組。  
  
### 檔案功能表群組  
  
|群組|ID|  
|--------|--------|  
|開啟新的 \/|IDG\_VS\_FILE\_FILE|  
|Add|IDG\_VS\_FILE\_ADD|  
|方案|IDG\_VS\_FILE\_SOLUTION|  
|其他|IDG\_VS\_FILE\_MISC|  
|儲存|IDG\_VS\_FILE\_SAVE|  
|重新命名|IDG\_VS\_FILE\_RENAME|  
|瀏覽器|IDG\_VS\_FILE\_BROWSER|  
|列印|IDG\_VS\_FILE\_PRINT|  
|最近使用的|IDG\_VS\_FILE\_MRU|  
|Move|IDG\_VS\_FILE\_MOVE|  
|結束|IDG\_VS\_FILE\_EXIT|  
  
### 編輯功能表群組  
  
|群組|ID|  
|--------|--------|  
|復原\/取消復原|IDG\_VS\_EDIT\_UNDOREDO|  
|剪下\/複製\/貼上|IDG\_VS\_EDIT\_CUTCOPY|  
|選取|IDG\_VS\_EDIT\_SELECT|  
|移至|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|物件|IDG\_VS\_EDIT\_OBJECTS|  
|OLE 動詞命令|IDG\_VS\_EDIT\_OLEVERBS|  
|命令的格式|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### 重構的功能表群組  
  
|群組|ID|  
|--------|--------|  
|通用|IDG\_REFACTORING\_COMMON|  
|進階|IDG\_REFACTORING\_ADVANCED|  
  
### 檢視功能表群組  
  
|群組|ID|  
|--------|--------|  
|表單程式碼|IDG\_VS\_VIEW\_FORMCODE|  
|瀏覽器|IDG\_VS\_VIEW\_BROWSER|  
|定義檢視|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Windows 架構設計人員|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|組織 Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|程式碼的瀏覽器|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Windows 開發人員|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|工具列|IDG\_VS\_VIEW\_TOOLBARS|  
|符號|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|瀏覽|IDG\_VS\_VIEW\_NAVIGATE|  
|小型瀏覽|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|物件瀏覽器|IDG\_VS\_VIEW\_OBJBRWSR|  
|命令的格式|IDG\_VS\_VIEW\_COMMANDWELL|  
|屬性頁|IDG\_VS\_VIEW\_PROPPAGES|  
|重新整理|IDG\_VS\_VIEW\_REFRESH|  
  
### 專案功能表群組  
  
|群組|ID|  
|--------|--------|  
|其他新增|IDG\_VS\_PROJ\_MISCADD|  
|Add|IDG\_VS\_PROJ\_ADD|  
|資料夾|IDG\_VS\_PROJ\_FOLDER|  
|卸除\/重新載入|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|參考資料|IDG\_VS\_PROJ\_REFERENCE|  
|選項|IDG\_VS\_PROJ\_OPTIONS|  
|設定|IDG\_VS\_PROJ\_SETTINGS|  
  
### 建置功能表群組  
  
|群組|ID|  
|--------|--------|  
|方案|IDG\_VS\_BUILD\_SOLUTION|  
|選取|IDG\_VS\_BUILD\_SELECTION|  
|特性指引最佳化|IDG\_VS\_PGO\_SELECTION|  
|其他|IDG\_VS\_BUILD\_MISC|  
|取消|IDG\_VS\_BUILD\_CANCEL|  
  
### 工具功能表群組  
  
|群組|ID|  
|--------|--------|  
|命令列|IDG\_VS\_TOOLS\_CMDLINE|  
|程式碼片段|IDG\_VS\_TOOLS\_SNIPPETS|  
|物件的子集|IDG\_VS\_TOOLS\_OBJSUBSET|  
|選項|IDG\_VS\_TOOLS\_OPTIONS|  
|其他 2|IDG\_VS\_TOOLS\_OTHER2|  
|外部工具|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|外部的自訂項目|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### 視窗功能表群組  
  
|群組|ID|  
|--------|--------|  
|新增|IDG\_VS\_WINDOW\_NEW|  
|停駐\/關閉|IDG\_VS\_DOCKCLOSE|  
|停駐\/隱藏|IDG\_VS\_DOCKHIDE|  
|排列|IDG\_VS\_WINDOW\_ARRANGE|  
|巡覽|IDG\_VS\_WINDOW\_NAVIGATION|  
|清單|IDG\_VS\_WINDOW\_LIST|  
  
### 說明功能表群組  
  
|群組|ID|  
|--------|--------|  
|範例|IDG\_VS\_HELP\_SAMPLES|  
|支援|IDG\_VS\_HELP\_SUPPORT|  
|關於|IDG\_VS\_HELP\_ABOUT|  
  
## Visual Studio 功能表的子功能表  
 下列階層會顯示在 Visual Studio 功能表列上的功能表與相關聯的子功能表。 只有群組都有功能表做為其父系，因為每一個子功能表必須下降從群組在功能表上，而不是直接從功能表。 如需功能表、 群組和子功能表之間的關聯性的詳細資訊，請參閱 [將子功能表新增至功能表](../../extensibility/adding-a-submenu-to-a-menu.md)。  
  
> [!NOTE]
>  在 Visual Studio 功能表列上的功能表名稱不會個別顯示此階層中因為他們可以從推斷群組在 IDE 中的命名慣例，如下所示: IDG\_VS\_*功能表名稱*\_*群組名稱*。  
  
|父群組|子功能表|子群組|  
|---------|----------|---------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1...6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## 請參閱  
 [Guid 和 Id 的 Visual Studio 工具列](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Guid 和 Id 的 Visual Studio 命令](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)