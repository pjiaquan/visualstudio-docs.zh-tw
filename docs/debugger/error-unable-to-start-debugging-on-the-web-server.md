---
title: "錯誤：無法在 Web 伺服器上啟動偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯工具, Web 應用程式錯誤"
  - "偵錯 [Visual Studio], 錯誤"
  - "偵錯 ASP.NET Web 應用程式, 無法啟動偵錯錯誤"
  - "錯誤 [偵錯工具], 無法啟動偵錯"
  - "HTTP 伺服器, 偵錯錯誤"
  - "IIS, 偵錯 DLL"
  - "遠端偵錯, 錯誤"
  - "安全性 [偵錯工具], Web 應用程式"
  - "安全性設定, 檢查預設的 Web 站台"
  - "無法啟動偵錯錯誤"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：無法在 Web 伺服器上啟動偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您嘗試偵錯 Web 伺服器上所執行的 ASP.NET 應用程式時，您可能會收到此錯誤訊息：無法在 Web 伺服器上開始偵錯。  
  
 在大部分情況下，此錯誤的發生原因為 IIS 未正確設定。  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> 請確定已正確設定 IIS  
 如需使用 MVC 5 應用程式部署到 IIS 8 的相關資訊，請參閱 [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)。  
  
 如需部署至 IIS7.5 的相關資訊，請參閱[在執行 IIS 7.5 的遠端電腦上遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> 請確定已安裝 Visual Studio 遠端工具  
 若您嘗試在遠端 Web 伺服器上偵錯，必須安裝 Visual Studio 遠端工具。 如需下載和設定遠端工具的相關資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> 請確定已安裝 ASP.NET  
 **IIS 8**  
  
 在 IIS 8 中，您會將 ASP.NET 安裝為 IIS 的一部分。  
  
1.  在 \[伺服器管理員\] 磚中，選取 \[儀表板\]，然後按一下 \[新增角色及功能\]。  
  
2.  在 \[安裝類型\] 頁面上，選取 \[角色型或功能型安裝\]，然後按一下 \[下一步\]。  
  
3.  在 \[選取目的地伺服器\] 頁面上，選取 \[從伺服器集區選取伺服器\]，選取您的伺服器，然後按一下 \[下一步\]。  
  
4.  在 \[選取伺服器角色\] 頁面上，選取 \[網頁伺服器 \(IIS\)\]，然後按一下 \[下一步\]。  
  
5.  在 \[選取功能\] 頁面上，按一下 \[下一步\]。  
  
6.  在 \[網頁伺服器角色 \(IIS\)\] 頁面上，按一下 \[下一步\]。  
  
7.  在 \[選取角色服務\] 頁面上，請注意預設會安裝之預先選取的角色服務，依序展開 \[應用程式伺服器\] 節點、\[.NET Framework 4.5\] 節點，然後再選取 \[ASP.NET 4.5\]。 \(若您安裝 .NET 3.5，請同時選取 \[ASP.NET 3.5\]。\)  
  
8.  在 \[確認安裝選項\] 頁面上，選擇 \[安裝\]。  
  
9. 在 \[安裝進度\] 頁面上，確認您的網頁伺服器 \(IIS\) 角色和必要的角色服務已成功完成安裝，然後按一下 \[關閉\]。  
  
 **IIS 7.5 和更早版本**  
  
 針對 IIS 7.5 或更早版本：從 \[命令提示字元\] 視窗中執行下列命令：  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## 基本的疑難排解  
 您可以透過以下方式，確定您的 ASP.NET 應用程式是否正確部署。  
  
## 在瀏覽器中顯示 localhost 頁面  
 若 IIS 未正確安裝，則您在瀏覽器中輸入 `http://localhost` 時應該會發生錯誤。  
  
## 在瀏覽器中顯示網頁  
 啟動網頁瀏覽器並輸入您嘗試偵錯之網頁的 URL \(例如：`http://localhost/MyWebApplication`\)。 若 IIS 未正確設定或 ASP.NET 應用程式未正確部署，則您應該會接收到錯誤，而該錯誤會協助您修正 IIS 設定和 ASP.NET 部署。  
  
## 在伺服器上建立基本的 ASP.NET 應用程式  
 請嘗試在本機伺服器上建立基本的 ASP.NET 應用程式，然後嘗試進行偵錯。  
  
## 若您只使用 IP 位址，請解決驗證錯誤  
 偵錯 Web 伺服器需要 NTLM 驗證 \(Authentication\)。 根據預設，IP 位址被假設為網際網路的一部分，且不會透過網際網路完成 NTLM 驗證。 若要修正這個問題，您可以指定遠端電腦的名稱。  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> 手動附加至處理序  
 若您開始偵錯時仍然出現錯誤訊息，建議您嘗試透過手動附加至處理序，進而偵錯您的應用程式。  
  
-   啟動應用程式但不進行偵錯 \(從 \[**偵錯**\] 功能表中，選擇 \[**啟動但不偵錯**\]\)。  
  
-   按一下 \[偵錯\/附加至處理序\]。  當視窗出現時，啟用 \[顯示所有使用者的處理序\]。  
  
-   尋找適當的處理序，然後進行附加。 針對 MVC 5 之前的 ASP.NET 應用程式，處理序為 w3wp.exe。 針對 MVC 5，請參閱 [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html)。  
  
## 請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)