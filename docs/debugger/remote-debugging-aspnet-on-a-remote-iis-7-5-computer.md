---
title: "在執行 IIS 7.5 的遠端電腦上遠端偵錯 ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在執行 IIS 7.5 的遠端電腦上遠端偵錯 ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以將 ASP.NET Web 應用程式部署至執行 IIS 7.5 的 Windows Server 2008 R2 電腦，然後設定該應用程式以進行遠端偵錯。 下列指示說明如何安裝和設定 Visual Studio 2015 MVC 4.5.2 應用程式。  
  
## 在 Visual Studio 電腦上建立應用程式  
  
1.  建立新的 MVC ASP.NET 應用程式。 \(\[檔案\] \/ \[新增\] \/ \[專案\]，然後選取 \[Visual C\#\] \/ \[Web\] \/ \[ASP.NET Web 應用程式\]。 在 \[ASP.NET 4.5.2\] 範本區段中選取 \[MVC\]。 取消 \[設定 Microsoft Azure Web App\] 頁面。 \) 並將它命名為 **MyMVC**。  
  
2.  開啟 HomeController.cs 檔案，並在 `About()` 方法中設定中斷點。  
  
3.  在 \[方案總管\]，以滑鼠右鍵按一下專案節點，然後選取 \[發行\]。  
  
4.  針對 \[選取發行目標\] 選取 \[自訂\]，然後將設定檔命名為 **MyMVC**。 按 \[下一步\]。  
  
5.  在 \[連接\] 索引標籤上，設定 \[發行方法\] 欄位為 \[檔案系統\]，以及設定 \[目標位置\] 欄位為本機目錄。 按 \[下一步\]。  
  
6.  設定要**偵錯**的組態。 按一下 \[發行\]。  
  
     應用程式應該要發行至本機目錄。  
  
## 在 Windows Server 遠端電腦上部署應用程式  
 本節假設此 Windows Server 2008 R2 電腦已啟用 IIS。  
  
1.  安裝 ASP.NET：  
  
     **C:\\Windows\\Microsoft.NET\\Framework\(64\)\\v4.0.30319\\aspnet\_regiis.exe \-ir**  
  
2.  將 ASP.NET 專案目錄從 Visual Studio 電腦複製到在 Windows 伺服器電腦上的本機目錄 \(我們將稱之為 **C:\\Publish**\)。  
  
3.  請確定 web.config 檔案會列出 .NET Framework 的正確版本。  在此電腦上預設安裝的 .NET Framework 版本是 4.0.30319，但是我們建立的是 ASP.NET 4.5.2 版本。 如果在此 Windows Server 電腦上未安裝此版本，則您需要變更版本：  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  開啟 \[Internet Information Services \(IIS\) 管理員\] 並移至 \[網站\]。  
  
5.  以滑鼠右鍵按一下 \[預設的網站\] 節點，並選取 \[加入應用程式\]。  
  
6.  將 \[別名\] 欄位設為 **MyMVC**，且將應用程式集區欄位設為 **ASP.NET v4.0**。 將 \[實體路徑\] 設定為 **C:\\Publish** \(您複製 ASP.NET 專案目錄的地方\)。  
  
7.  若要測試部署，以滑鼠右鍵按一下 \[預設的網站\]，然後選取 \[瀏覽\]。 您應該會看到此網頁。  
  
## 在 Windows Server 電腦上安裝遠端偵錯工具  
 如需有關如何下載遠端偵錯工具的指示，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
 若要遠端偵錯 ASP.NET 應用程式，您可以啟動遠端偵錯工具為服務，或以系統管理員身分執行遠端偵錯工具應用程式。 如需如何將遠端偵錯工具做為服務執行的詳細資料，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
## 從 Visual Studio 電腦連接至 ASP.NET 應用程式  
  
-   在 Visual Studio 電腦上開啟 \[MyMVC\] 方案。  
  
-   在 Visual Studio 按一下 \[偵錯\] \/ \[附加至處理序\]。  
  
-   將 \[限定詞\] 欄位設定為 **\<遠端電腦名稱\>: 4020**。  
  
-   您應該會看到有些處理程序會出現在 \[可使用的處理序\] 視窗。  
  
-   核取 \[顯示所有使用者的處理序\]。  
  
-   尋找 **w3wp.exe**，然後按一下 \[附加\]。  
  
-   開啟遠端電腦的網站。 在瀏覽器中，移至 **http:\/\/\<遠端電腦名稱 \>**。  
  
-   您應該會看到 ASP.NET 網頁。 按一下 \[關於\]。  
  
     應該在 Visual Studio 中叫用中斷點。