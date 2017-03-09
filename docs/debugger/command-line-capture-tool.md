---
title: "命令列擷取工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 命令列擷取工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DXCap.exe 是圖形診斷擷取及播放的命令列工具。  它支援 Direct3D 10 到 Direct3D 12 的所有功能層級。  
  
## 語法  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### 參數  
 `-file` `filename`  
 在擷取模式下 \(`-c`\)，`filename` 會指定圖形資訊記錄到的圖形記錄檔名稱。  如果未指定 `filename`，圖形資訊預設會記錄到名為 `<appname>-<date>-<time>.vsglog` 的檔案。  
  
 在驗證 \(\-v\) 模式中，`filename` 指定要驗證的圖形記錄檔名稱。  如果未指定 `filename`，會再次使用前次驗證的圖形記錄檔。  
  
 `-frame` `frames`  
 在擷取模式下，`frames` 指定您想要擷取的框架。  第一個框架為 1。  您可以使用逗號和範圍來指定多個框架。  例如，如果 `frames` 是 `2, 5, 7-9, 15`，則會擷取框架 `2`、`5`、`7`、`8`、`9` 和 `15`。  
  
 `-期間` `periods`  
 在擷取模式下，`periods` 指定您要擷取框架的時間範圍，以秒為單位。  您可以使用逗號和範圍來指定多個期間。  例如，如果 `periods` 是 `2.1-5, 7.0-9.3`，則會擷取 `2.1` 和 `5` 秒之間呈現的框架，以及 `7` 和 `9.3` 秒之間呈現的框架。  
  
 `-manual`  
 在擷取模式下，`-manual` 指定框架將會藉由按下 Print Screen 鍵以手動方式擷取。  應用程式啟動時，就可以擷取框架；若要停止擷取框架，請返回到命令列介面並按下 Enter 鍵。  
  
 `-c` `app` \[`args...`\]  
 擷取模式。  在擷取模式下，`app` 指定您想要從其中擷取圖形資訊的應用程式名稱；`args...` 指定該應用程式的其他命令列參數。  
  
 `-p` \[`filename`\]  
 播放模式 \(`-p`\)。  在播放模式中，`filename` 指定要播放的圖形記錄檔名稱。  如果未指定 `filename`，會再次使用前次播放的圖形記錄檔。  
  
 `-debug`  
 在播放模式中，`-debug` 指定播放執行時應該啟用 Direct3D 偵錯層。  
  
 `-warp`  
 在播放模式中，`-warp` 指定應該使用 WARP 軟體呈現器執行播放。  
  
 `-hw`  
 在播放模式中，`-hw` 指定應該使用 GPU 硬體執行播放。  
  
 `-config`  
 在播放模式中，`-config` 會顯示用來擷取圖形記錄檔的機器相關資訊 \(如果這項資訊記錄到記錄檔\)。  
  
 `-rawmode`  
 在播放模式中，`-rawmode` 指定執行播放時應該不修改記錄的事件。  在正常操作下，播放模式可能會對播放進行次要變更，以簡化偵錯，並加快播放的速度。  例如，它可能會模擬交換鏈結輸出，而不是執行交換鏈結命令。  通常這並不是問題，但您可能需要讓播放時更忠實呈現記錄的事件；例如，您可以使用這個選項來以全螢幕呈現行為，還原至以全螢幕模式執行時擷取的應用程式。  
  
 `-toXML` \[`xml_filename`\]  
 在播放模式中，`xml_filename` 指定 XML 代表寫入的播放檔案名稱。  如果 `xml_filename` 未指定，XML 代表將會寫入一個名稱與播放中檔案相同的檔案，但其具有 `.xml` 副檔名。  
  
 `-v`  
 驗證模式。  在驗證模式下，所擷取的框架會在硬體和 WARP 上播放，並會使用影像比較函式來比較它們的結果。  您可以使用這項功能，來快速找出影響您呈現的驅動程式問題。  
  
 `-examine` `events`  
 在驗證模式下，`events` 指定會比較其立即結果的圖形事件集。  例如，`-examine present,draw,copy,clear` 將比較限制在只有屬於那些類別的事件。  
  
> [!TIP]
>  我們建議您從 `-examine present,draw,copy,clear` 開始，因為這會顯示大部分的問題，但是所需的時間比更廣泛的事件集大幅縮短。  如有必要，您可以指定較大或不同的事件集來驗證這些事件，並且顯示其他種類的問題。  
  
 `-haltonfail`  
 在驗證模式下，`-haltonfail` 會在硬體和 WARP 轉譯器之間偵測到差異時，中止驗證。  按下按鍵之後，會繼續執行驗證。  
  
 `-exitonfail`  
 在驗證模式下，`-exitonfail` 會在硬體和 WARP 轉譯器之間偵測到差異時，立即結束驗證。  當以這種方式結束程式時，它會傳回 `0` 給環境；否則它會傳回 `1`。  
  
 `-showprogress`  
 在驗證模式下，`-showprogress` 會顯示驗證工作階段的進度資訊。  WARP 進度顯示在左邊，而硬體進度顯示在右邊。  
  
 `-e` `search_string`  
 列舉已安裝的 Windows 市集應用程式。  您可以使用這項資訊來執行 Windows 市集應用程式的命令列擷取。  
  
 `-info`  
 顯示電腦的相關資訊，並擷取 DLL。  
  
## 備註  
 DXCap.exe 有三種操作模式：  
  
 擷取模式 \(\-c\)  
 擷取正在執行的應用程式中的圖形資訊，並將它記錄到圖形記錄檔。  擷取功能及檔案格式與 Visual Studio 的完全相同。  
  
 播放模式 \(\-p\)  
 從現有的圖形記錄檔播放先前所擷取的圖形事件。  根據預設會以視窗播放，即使圖形記錄檔是從全螢幕應用程式擷取也一樣。  只有當圖形記錄檔是從全螢幕應用程式擷取，且指定 `-rawmode` 時才會以全螢幕播放。  
  
 驗證模式 \(`-v`\)  
 藉由在硬體和 WARP 播放擷取的框架，然後使用影像比較功能比較它們的結果，來驗證轉譯行為。  您可以使用這項功能，來快速找出影響您呈現的驅動程式問題。  
  
 除了這些模式，dxcap.exe 還會執行其他兩個不會擷取或播放圖形資訊的功能。  
  
 列舉功能 \(`-e`\)  
 顯示電腦上安裝的 Windows 市集應用程式的詳細資料。  這些詳細資料包含套件名稱和識別 Windows 市集應用程式中的可執行檔的 appid。  若要使用 DXCap.exe 擷取來自 Windows 市集應用程式的圖形資訊，請使用套件名稱和 appid，而不是擷取桌面應用程式時使用的可執行檔名稱。  
  
 資訊功能 \(`-info)`  
 顯示電腦的詳細資料，並擷取 DLL。  
  
## 範例  
  
### 擷取桌面應用程式中的圖形資訊  
 使用 `– c` 來指定您要擷取圖形資訊的應用程式。  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 圖形資訊預設會記錄到名為 `<appname>-<date>-<time>.vsglog` 的檔案。  使用 `–file` 來指定記錄到不同的檔案。  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 指定您正在從中擷取的應用程式的其他命令列參數，將它們包括在應用程式的檔名之後。  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 在上述範例中的命令會在檢視位於 www.fishgl.com 的網頁時，擷取 Internet Explorer 桌面版本的圖形資訊；該網頁使用 WebGL API 來呈現 3d 內容。  
  
> [!NOTE]
>  因為應用程式之後出現的命令列引數會傳遞給它，您必須指定適用於 DXCap.exe 的引數，然後才能使用 `–c` 選項。  
  
### 擷取來自 Windows 市集應用程式的圖形資訊。  
 您可以擷取來自 Windows 市集應用程式的圖形資訊。  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 使用 DXCap.exe 來擷取 Windows 市集應用程式，類似於使用它來擷取從 Windows 桌面應用程式，但您不會依檔名識別桌面應用程式，而是依套件名稱和您要擷取之套件內的可執行檔名稱或識別碼來識別 Windows 市集應用程式。  若要更容易了解如何識別電腦上安裝的 Windows 市集應用程式，請使用 `–e` 選項搭配 DXCap.exe 來列舉它們：  
  
```ms-dos  
DXCap.exe -e  
```  
  
 您可以提供選擇性的搜尋字串，以協助找出您要尋找的應用程式。  提供搜尋字串時，DXCap.exe 會列舉套件名稱、應用程式名稱或應用程式識別碼符合搜尋字串的 Windows 市集應用程式。  搜尋不區分大小寫。  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 上述命令會列舉符合 "map" 的 Windows 市集應用程式。輸出如下：  
  
  **Package "Microsoft.BingMaps":**  
 **InstallDirectory : C:\\Program Files\\WindowsApps\\Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe**  
 **FullName         : Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe**  
 **UserSID          : S\-1\-5\-21\-2127521184\-1604012920\-1887927527\-5603533**  
 **Name             : Microsoft.BingMaps**  
 **Publisher        : CN\=Microsoft Corporation, O\=Microsoft Corporation, L\=Redmond, S\=Washington, C\=US**  
 **Version          : 2.1.2914.1734**  
 **可啟動的應用程式︰**  
 **Id   : AppexMaps**  
 **Exe  : C:\\Program Files\\WindowsApps\\Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe\\Map.exe**  
 **IsWWA: No**  
 **AppSpec \(以啟動\): **DXCap.exe \-c Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe,AppexMaps****  每個列舉的應用程式輸出最後一行會顯示您可用來從其中擷取圖形資訊的命令。  
  
### 擷取特定框架或特定時間之間的框架。  
 使用 `–frame` 來使用逗點和範圍指定您想要擷取的框架：  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 或者，您也可以使用 `–period`，以指定要擷取框架的時間範圍集。  時間範圍以秒為指定單位，且您可以指定多個範圍：  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### 以互動方式擷取框架。  
 使用 `–manual` 以互動方式擷取框架。  按下 Enter 鍵開始擷取，然後再按一次 Enter 鍵停止。  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### 播放圖形記錄檔  
 使用 `-p` 播放先前所擷取的圖形記錄檔。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 排除播放最近擷取的圖形記錄檔檔名。  
  
```ms-dos  
DXCap.exe –p  
```  
  
### 在原始模式中播放  
 使用 `-rawmode` 以擷取的命令發生時的確切狀況播放。  在正常播放下，某些命令是經過模擬的，例如，從全螢幕應用程式擷取的圖形記錄檔將在視窗中播放；啟用原始模式時，相同的檔案將會嘗試以全螢幕播放。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### 使用 WARP 或硬體裝置播放  
 您可能想要在硬體裝置上強制使用 WARP 播放擷取的圖形記錄檔，或是強制使用硬體裝置播放在 WARP 上擷取的記錄檔。  使用 `-warp` 以 WARP 進行播放。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 使用 `-hw` 以硬體進行播放。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### 針對 WARP 驗證圖形記錄檔  
 在驗證模式中，圖形記錄檔會在硬體和 WARP 上播放，並比較其結果。  這可以協助您識別驅動程式所造成的轉譯錯誤。  使用 \-v 來針對 WARP 驗證圖形硬體的正確行為。  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 若要減少比較次數，您可以指定驗證要比較的命令子集，將會忽略其他命令。  使用 –examine 指定您想要比較其結果的命令。  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### 將圖形記錄檔轉換成 PNG  
 若要檢視或分析圖形記錄檔中的框架，DXCap.exe 可以將擷取的框架儲存為 .png \(可攜式網路圖形\) 影像檔。  使用 `-screenshot` 在播放模式下，將擷取的框架輸出為 .png 檔案。  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 使用 `–frame` 和 `–screenshot` 指定您要輸出的框架。  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### 將圖形記錄檔轉換成 XML  
 若要使用熟悉的工具，如 FindStr 或 XSLT 處理及分析圖形記錄檔，DXCap.exe 可以將圖形記錄檔轉換成 XML。  使用 `-toXML` 在播放模式下將記錄檔轉換成 XML，而非播放它。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 根據預設，XML 輸出會寫入至與圖形記錄檔同名的檔案，但它具有 .xml 副檔名。  在上述範例中，XML 檔案的名稱會是 **regression\_test\_12.xml**。  若要讓 XML 檔案有不同的名稱，請指定在 `-toXML` 之後。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 產生的檔案會包含類似如下的 XML：  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## 需求