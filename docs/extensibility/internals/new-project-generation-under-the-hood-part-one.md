---
title: "新產生的專案︰ 在幕後，第一部 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio]，新增專案] 對話方塊"
  - "專案 [Visual Studio]，新的專案產生"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 新產生的專案︰ 在幕後，第一部
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您曾經想過如何建立您自己的專案類型嗎？ 不知道實際發生的狀況時建立新的專案？ 讓我們來看一下底下，查看真的發生什麼。  
  
 有幾個 Visual Studio 協調您的工作︰  
  
-   它會顯示所有可用的專案類型的樹狀結構。  
  
-   它會顯示每個專案類型的應用程式範本的清單，並讓您挑選其中一個。  
  
-   它會收集應用程式，例如專案名稱和路徑的專案資訊。  
  
-   它會將這項資訊傳遞專案的處理站。  
  
-   它會在目前方案中產生專案項目和資料夾。  
  
## 新增專案對話方塊  
 所有您選取新的專案的專案類型時開始。 讓我們開始依序按一下 **新的專案** 上 **檔案** 功能表。**新的專案** 對話方塊隨即出現，看起來如下所示︰  
  
 ![新增專案對話方塊](~/docs/extensibility/internals/media/newproject.gif "NewProject")  
  
 讓我們仔細看。**專案類型** 樹狀目錄會列出您可以建立各種專案類型。 當您選取專案類型，如 **Visual C\# Windows**, ，您會看到您的應用程式範本的清單。**Visual Studio 安裝的範本** 由 Visual Studio 安裝，而且可供您電腦的任何使用者。 可以加入新的範本所建立，或收集 **我的範本** 和只提供給您。  
  
 當您選取的範本，例如 **Windows 應用程式**, ，應用程式類型的描述會出現在對話方塊中，在此情況下， **與 Windows 使用者介面建立應用程式的專案**。  
  
 在底部 **新的專案** 對話方塊中，您會看到幾個收集的詳細資訊的控制項。 控制項，您會看到依存於專案類型，但它們通常包含專案 **名稱** \] 文字方塊中， **位置** 文字方塊和相關 **瀏覽** \] 按鈕，和 **方案名稱** 文字方塊和相關 **為方案建立目錄** 核取方塊。  
  
## 填入新的 \[專案\] 對話方塊  
 其中沒有 **新的專案** 對話方塊取得的資訊嗎？ 在這裡，其中一個已被取代的有兩種機制。**新的專案** 對話方塊結合，並顯示這兩種機制從取得的資訊。  
  
 較舊的 （已過時） 方法會使用系統登錄項目和.vsdir 檔案。 Visual Studio 開啟時，就會執行這項機制。 較新的方法會使用.vstemplate 檔案。 這項機制會在 Visual Studio，比方說，以初始化時執行  
  
```  
devenv /setup  
```  
  
 或  
  
```  
devenv /installvstemplates  
```  
  
### 專案類型  
 位置和名稱 **專案類型** 根節點，例如 **Visual C\#** 和 **其他語言**, ，取決於系統登錄項目。 組織的子節點，例如 **資料庫** 和 **智慧型裝置**, ，鏡像處理包含對應的.vstemplate 檔案的資料夾階層。 讓我們先看看根節點。  
  
#### 專案類型的根節點  
 當 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是初始化，周遊系統登錄機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs 若要建置和名稱的根節點的子機碼 **專案類型** 樹狀結構。 這項資訊會快取以供稍後使用。 看看 TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC} \\\/1 索引鍵。 每個項目是 VSPackage 的 GUID。 子機碼的名稱 （\/ 1） 會被忽略，但其目前狀態，表示這是 **專案類型** 根節點。 根節點也可能有子機碼控制其外觀 **專案類型** 樹狀結構。 讓我們看看其中部分。  
  
##### \(預設值\)  
 這是名稱的根節點的當地語系化字串的資源識別碼。 字串資源位於附屬 DLL 選取的 VSPackage GUID。  
  
 在範例中，為 VSPackage GUID  
  
 {} FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC  
  
 根節點的資源識別碼 （預設值） 和 （\/ 1） 為 \# 2345年  
  
 如果您查詢中鄰近的封裝金鑰的 GUID，並檢查 SatelliteDll 子機碼，您可以找到包含字串資源的組件的路徑︰  
  
 \< visual Studio 安裝路徑 \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 若要驗證這一點，開啟 \[檔案總管\] 並將 csprojui.dll 到 Visual Studio 目錄... 字串資料表會顯示資源 \# 2345年有標題 **Visual C\#**。  
  
##### SortPriority  
 這會決定的位置中的根節點 **專案類型** 樹狀結構。  
  
 SortPriority REG\_DWORD 0x00000014 \(20\)  
  
 越低優先權的數字越高樹狀目錄中的位置。  
  
##### DeveloperActivity  
 如果這個子機碼存在，則根節點的位置由開發者設定\] 對話方塊所控制。 例如：  
  
 DeveloperActivity REG\_SZ VC \#  
  
 表示 Visual C\# 將根節點如果 Visual Studio 為 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 開發。 否則，它是子節點的 **其他語言**。  
  
##### 資料夾  
 如果這個子機碼存在，根節點就會成為指定的資料夾的子節點。 可能的資料夾清單隨即出現在機碼  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 比方說，資料庫專案項目具有符合其他專案類型中的項目 PseudoFolders 資料夾索引鍵。 因此，在 **專案類型** 樹狀目錄中， **資料庫專案** 將成為子節點 **其他專案類型**。  
  
#### 專案類型的子節點和.vstdir 檔案  
 中的子節點的位置 **專案類型** 樹狀結構會遵循 ProjectTemplates 資料夾中的資料夾階層。 針對機器範本 \(**Visual Studio 安裝的範本**\)，一般位置是 files\\microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\，並提供使用者範本 \(**我的範本**\)，一般位置是 documents\\visual Studio 14.0\\Templates\\ProjectTemplates\\。 從這兩個位置的資料夾階層會合併，以建立 **專案類型** 樹狀結構。  
  
 Visual Studio C\# 開發者設定，如 **專案類型** 樹狀結構看起來像這樣︰  
  
 ![專案類型](~/docs/extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 相對應的 ProjectTemplates 資料夾看起來像這樣︰  
  
 ![專案範本](~/docs/extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 當 **新的專案** 對話方塊隨即開啟， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 周遊 ProjectTemplates 資料夾，並重新建立它的結構中 **專案類型** 樹狀目錄中的有一些變更︰  
  
-   中的根節點 **專案類型** 樹狀結構由應用程式範本。  
  
-   節點名稱可以當地語系化，而且可以包含特殊字元。  
  
-   可變更排序次序。  
  
##### 尋找專案類型的根節點  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會開啟所有的.zip 檔案，並擷取任何.vstemplate 檔案。 .Vstemplate 檔案使用 XML 來描述應用程式範本。 如需詳細資訊，請參閱[新產生的專案: 在幕後，第二部](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)。  
  
 \< ProjectType \> 標記判斷應用程式的專案類型。 例如，\\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip 檔案包含具有此標記的 EmptyProject.vstemplate 檔案︰  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \< ProjectType \> 標記，並不在 ProjectTemplates 資料夾中，子資料夾會決定在應用程式的根節點 **專案類型** 樹狀結構。 在範例中，Windows CE 應用程式就會出現在 **Visual C\#** 根節點，而且即使您是要將 WindowsCE 資料夾移至 \[visual Basic\] 資料夾，Windows CE 應用程式仍會出現在 **Visual C\#** 根節點。  
  
##### 當地語系化的節點名稱  
 當 Visual Studio 會周遊 ProjectTemplates 資料夾時，它會檢查它所找到的任何.vstdir 檔案。 .Vstdir 檔案是 XML 檔案，以控制專案類型中的外觀 **新的專案** 對話方塊。 在.vstdir 檔案中，使用 \[\< LocalizedName \> 標記名稱 **專案類型** 節點。  
  
 例如，\\CSharp\\Database\\TemplateIndex.vstdir 檔案包含此標記︰  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 這會決定名稱的根節點，在此情況下，當地語系化字串的附屬 DLL 和資源識別碼 **資料庫**。 當地語系化的名稱可以包含特殊字元，並不適用於資料夾名稱，例如 **.NET**。  
  
 如果沒有 \< LocalizedName \> 標記，由資料夾本身，名為專案類型 **SmartPhone2003**。  
  
##### 尋找專案類型的排序順序  
 若要判斷專案類型的排序次序，.vstdir 檔案會使用 \< SortOrder \> 標記。  
  
 例如，\\CSharp\\Windows\\Windows.vstdir 檔案包含此標記︰  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \\CSharp\\Database\\TemplateIndex.vstdir 檔案包含具有較大的值的標記︰  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 \< SortOrder \> 中的數字愈低標記，請在樹狀目錄中的高位置使 **Windows** 節點會出現高於 **資料庫** 節點 **專案類型** 樹狀結構。  
  
 如果未指定 \< SortOrder \> 標記，為專案類型，它會以下列包含 \< SortOrder \> 規格任何專案類型的字母順序顯示。  
  
 請注意我的文件中沒有.vstdir 檔案 \(**我的範本**\) 資料夾。 未當地語系化使用者應用程式專案型別名稱，並依字母順序顯示。  
  
#### 快速檢閱  
 我們要修改 **新的專案** 對話方塊並且建立新的使用者專案範本。  
  
1.  Files\\microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp 資料夾中新增 MyProjectNode 子資料夾。  
  
2.  使用任何文字編輯器的 MyProjectNode 資料夾中建立 MyProject.vstdir 檔案。  
  
3.  .Vstdir 檔案中加入下列幾行︰  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  儲存並關閉.vstdir 檔案。  
  
5.  使用任何文字編輯器的 MyProjectNode 資料夾中建立 MyProject.vstemplate 檔案。  
  
6.  .Vstemplate 檔案中加入下列幾行︰  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  儲存 the.vstemplate 檔案，並關閉編輯器。  
  
8.  .vstemplate 檔案傳送給新的壓縮 MyProjectNode\\MyProject.zip 資料夾。  
  
9. 從 Visual Studio 命令視窗中，輸入︰  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 開啟 Visual Studio。  
  
1.  開啟 **新的專案** \] 對話方塊中，展開 \[ **Visual C\#** 專案節點。  
  
 ![MyProjectNode](~/docs/extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** 會顯示為子節點的 Visual C\# Windows 節點的下方。  
  
## 請參閱  
 [新產生的專案: 在幕後，第二部](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)