---
title: "註冊專案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，新專案的登錄項目"
  - "登錄中，新的專案類型"
  - "註冊新的專案類型"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# 註冊專案類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您建立新的專案類型時，您必須先建立登錄項目，可讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]辨識並處理您的專案類型。  您通常會藉由使用登錄指令碼 \(.rgs\) 檔建立這些登錄項目。  
  
 在下面範例中，從登錄的陳述式提供的預設路徑，資料可以使用的話，後面跟著一個資料表包含每一個陳述式的登錄指令碼中的項目。  資料表會提供指令碼項目和陳述式的其他資訊。  
  
> [!NOTE]
>  下列的登錄資訊被要類型的範例，方便您將需要撰寫要註冊您的專案類型的登錄指令碼中的項目。  您的實際項目，以及它們的用法可能因專案類型的特定需求。  您應檢閱可用來尋找相似的您開發的專案類型的其中一個範例，再接著檢閱該範例中的登錄指令碼。  
  
 下列範例是從 HKEY\_CLASSES\_ROOT。  
  
## 範例  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`FigPrjFile`|名稱和描述專案的型別具有副檔名.figp 的檔案。|  
|`Content Type`|REG\_SZ|`Text/plain`|專案檔的內容類型。|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|這種類型的專案所使用的預設圖示。  %MODULE%的陳述式已完成登錄的 DLL 的專案類型的預設位置中。|  
|`@`|REG\_SZ|`&Open in Visual Studio`|將會開啟這個專案類型的預設應用程式。|  
|`@`|REG\_SZ|`devenv.exe "%1"`|預設會在這種類型的專案開啟時執行的命令。|  
  
 下列範例來自作用中計時間，並位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\99.0Exp\\Packages\] 下。  
  
## 範例  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@` \(預設值\)|REG\_SZ|`FigPrj Project VSPackage`|可當地語系化的名稱，此登錄 VSPackage \(專案型別\)。|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|專案類型 DLL 的路徑。  IDE 載入這個 DLL，並傳遞至 VSPackage CLSID `DllGetClassObject`以取得<xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory>來建構<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>物件。|  
|`CompanyName`|REG\_SZ|`Microsoft`|開發專案類型之公司的名稱。|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|專案型別的名稱。|  
|`ProductVersion`|REG\_SZ|`9.0`|已發行的版本號碼的專案類型。|  
|`MinEdition`|REG\_SZ|`professional`|所註冊的 VSPackage 版本。|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|套件載入專案 VSPackage 的機碼。  當載入專案時啟動環境後，索引鍵會進行驗證。|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|附屬 DLL，其中包含 \[專案類型的當地語系化的資源檔名。|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|附屬 DLL 的路徑。|  
|`FigProjectsEvents`|REG\_SZ|請參閱值的陳述式。|決定針對此自動化事件所傳回的文字字串。|  
|`FigProjectItemsEvents`|REG\_SZ|請參閱值的陳述式。|決定針對此自動化事件所傳回的文字字串。|  
  
 所有下列的範例都位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\] 下。  
  
## 範例  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`FigPrj Project`|這種類型的專案的預設名稱。|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|在 \[封裝\] 下，從附屬 DLL 中擷取的資源識別碼的名稱登錄。|  
|`Package`|REG\_SZ|`%CLSID_Package%`|在 \[封裝\] 下，登錄類別識別碼的 VSPackage。|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|預設的專案範本檔案的路徑。  這些都是新的專案範本所顯示的檔案。|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|預設的專案項目範本檔案的路徑。  這些都是由加入新項目範本所顯示的檔案。|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|若要實作 IDE 會啟用**開啟**對話方塊。|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|使用 IDE 來決定正在開啟的專案由這種專案類型 \(專案工廠\)。  多個項目格式是以分號分隔清單。  例如"vdproj; vdp"。|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|用於 ide 做為預設檔案名稱副檔名另存新檔作業。|  
|`Filter Settings`|REG\_DWORD|各種項目，請參閱陳述式和表格後的註解。|這些設定用來設定各種 UI\] 對話方塊中顯示的檔案篩選條件。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|加入項目範本的資源識別碼。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|顯示在對話方塊中的專案項目路徑**加入新項目**範本。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|樹狀節點中顯示的檔案中的排序順序會決定**加入新項目**對話方塊。|  
  
 下表顯示篩選器可用的選項在先前的程式碼片段。  
  
|篩選器\] 選項|描述|  
|--------------|--------|  
|`CommonFindFilesFilter`|表示篩選器是其中一個常見的篩選器，在**檔案中尋找**對話方塊。  未標記為常見的篩選器在目前的篩選器清單列出通用的篩選器。|  
|`CommonOpenFilesFilter`|表示篩選器是其中一個常見的篩選器，在**開啟的檔案**對話方塊。  未標記為常見的篩選器在目前的篩選器清單列出通用的篩選器。|  
|`FindInFilesFilter`|表示篩選器將其中一個篩選器，在**檔案中尋找**對話方塊方塊，然後將列在 \[一般篩選器之後。|  
|`NotOpenFileFilter`|表示篩選器中將不會使用**開啟的檔案**對話方塊。|  
|`NotAddExistingItemFilter`|表示篩選器不會使用在 \[新增**現有項目**對話方塊。|  
  
 預設情況下，如果篩選器並沒有一個或多個這些旗標的集合，篩選器會用來**加入現有項目** \] 對話方塊中， **開啟的檔案**之後列出通用的篩選器\] 對話方塊。  篩選器不會用於**檔案中尋找**對話方塊。  
  
 所有下列的範例都位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\] 下。  
  
## 範例  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|新的專案範本的資源識別碼。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|預設已註冊的專案類型的專案的路徑。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|集合的排序順序顯示在新專案精靈\] 對話方塊中的專案。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 表示只能在 \[新增專案\] 對話方塊中顯示的這種類型的專案。|  
  
 所有下列的範例都位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\] 下。  
  
## 範例  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|None|預設值，表示下列項目是針對其他檔案專案項目。|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|加入新項目範本檔的資源 ID 值。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|將會顯示在項目的預設路徑**加入新項目**對話方塊。|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|建立排序順序，顯示在樹狀節點的**加入新項目**對話方塊。|  
  
 下列範例位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Menus\] 下。  
  
## 範例  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 功能表項目會指向用來擷取功能表資訊的資源中的 IDE。  當功能表資料庫已經合併此資料時，相同的金鑰將會加入登錄中的 \[MenusMerged\] 區段中。  VSPackage 不應修改 \[MenusMerged\] 區段下的任何項目直接。  下表中的 \[資料\] 欄位中，有三個逗點\-分隔的欄位。  第一個欄位會識別功能表資源檔的完整路徑：  
  
-   如果省略第一個欄位，則從附屬 DLL 是由 VSPackage GUID 識別載入功能表資源。  
  
 第二個欄位會識別型別 CTMENU 的功能表資源的識別碼:  
  
-   如果指定的資源識別碼，而且檔案路徑由所提供的第一個參數，從完整檔案路徑載入功能表資源。  
  
-   如果提供的資源識別碼，但檔案路徑不是，功能表資源將從附屬 DLL 載入。  
  
-   如果提供的完整檔案路徑的資源 ID 省略，cto 能夠檔案，也可以預期要載入檔案。  
  
 最後一個欄位識別版本號碼為 CTMENU 的資源。  您可以藉由變更的版本號碼，一次合併功能表。  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|%Clsid\_package%|REG\_SZ|`,1000,1`|要擷取功能表資訊的資源。|  
  
 所有下列的範例都位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\NewProjectTemplates\] 下。  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|取得專案新專案時，圖表範本的資源 ID 值。|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|新的專案目錄的預設路徑。  這個目錄中的項目會顯示在**新專案精靈**對話方塊。|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|建立的專案將會顯示在樹狀節點的順序**新的專案**對話方塊。|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 表示這種類型的專案會僅在顯示**新的專案**對話方塊。|  
  
 下列範例位於登錄機碼 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\InstalledProducts\] 下。  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|已註冊的 VSPackage 類別 ID。|  
|`UseInterface`|REG\_DWORD|`1`|1 表示 UI 將用於此專案進行互動。  0 表示沒有 UI 介面。|  
  
 控制新的專案類型常用的 The.vsz 檔案包含 RELATIVE\_PATH 項目。  此路徑是相對於指定的專案類型，將下列的安裝程式機碼的 \\ProductDir 項目之下的路徑：  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup  
  
 例如，企業架構專案範本會加入下列的登錄項目：  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup\\EF\\ProductDir \= 檔必要視覺化 Studio\\EnterpriseFrameworks\\  
  
 這表示如果您包含 PROJECT\_TYPE \= EF 在.vsz 檔中，您的.vsz 檔案之前指定的 ProductDir 目錄中的環境尋找的項目。  
  
## 請參閱  
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)   
 [使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)