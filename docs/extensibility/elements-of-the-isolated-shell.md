---
title: "獨立 Shell 的項目 | Microsoft Docs"
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
  - "Visual Studio shell，隔離模式"
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 獨立 Shell 的項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以修改登錄設定、 執行階段設定，以及獨立的 shell 應用程式，其.vsct、.pkgdef、 and.pkgundef 檔案的應用程式進入點。  
  
## 登錄設定  
 .pkgdef 和.pkgundef 檔案修改獨立的 shell 應用程式的登錄設定。 當應用程式執行時，登錄設定定義以下列順序︰  
  
 當應用程式執行時，登錄設定定義以下列順序︰  
  
1.  建立應用程式的登錄機碼。  
  
2.  藉由指定之索引鍵和項目定義的.pkgdef 檔案中的應用程式更新登錄。  
  
3.  針對屬於您的應用程式的每個套件，會從.pkgdef 檔案，該封裝的更新登錄。 每個封裝應用程式的.pkgdef 檔中定義 $RootKey$ \\Packages\\ {*vsPackageGuid*} 套件的金鑰。  
  
4.  會更新登錄中的 BaseConfig.pkgdef AppEnvConfig.pkgdef 與 *Visual Studio SDK 安裝路徑*\\Common7\\IDE\\ShellExtensions\\Platform 目錄。 這些檔案是 Visual Studio 的一部分，也是 Visual Studio Shell （獨立的模式） 可轉散發套件的一部分。  
  
5.  .Pkgundef 檔案的應用程式會更新登錄，藉由移除指定的索引鍵和項目。  
  
## 執行階段設定  
 當使用者開始獨立的 shell 應用程式時，它會呼叫 Visual Studio shell 的開始進入點。 應用程式設定會定義您的應用程式啟動時，，如下所示︰  
  
1.  Visual Studio shell 會檢查特定機碼的應用程式登錄。 如果開始進入點的呼叫中指定的索引鍵的設定，則該值會覆寫登錄中的值。  
  
2.  登錄或項目都不如果參數會指定一個設定值，就會使用預設值，此設定。  
  
 當使用者從命令列啟動您的應用程式時，所有的命令列參數會傳遞至 Visual Studio shell 將它們視為相同的方式，Devenv 會執行。 如需 Devenv 參數的詳細資訊，請參閱 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md) 和 [VSPackage 開發 Devenv 命令列參數](../extensibility/devenv-command-line-switches-for-vspackage-development.md)。 如需封裝的命令列參數的暫存器的詳細資訊，請參閱 [加入命令列參數](../extensibility/adding-command-line-switches.md)。  
  
## 開始進入點  
 Appenvstub.dll 檔案包含存取獨立的 shell 的進入點。 當應用程式啟動時，它會呼叫開始進入點的 Appenvstub.dll。  
  
 您可以變更應用程式的行為變更傳遞給開始進入點的最後一個參數的值。 如需詳細資訊，請參閱[獨立的 Shell 進入點參數 \(c \+ \+\)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)。  
  
## 。Vsct 檔案  
 .Vsct 檔可讓您指定應用程式中可用的標準 Visual Studio UI 項目。 如需詳細資訊，請參閱[.Vsct 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)。  
  
## 。Pkgundef 檔案  
 在其已安裝 Visual Studio 的電腦上安裝應用程式時，一份 Visual Studio 登錄項目是針對應用程式。 根據預設，應用程式會使用已安裝在電腦的 Vspackage。 .Pkgundef 檔案可讓您排除以便從應用程式中移除之特定元素的 Visual Studio shell 或延伸模組的登錄項目。 如需詳細資訊，請參閱[.Pkgundef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 .Pkgundef 檔案可讓您排除以便從應用程式中移除之特定元素的 Visual Studio shell 或延伸模組的登錄項目。 如需詳細資訊，請參閱[.Pkgundef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 中所列的封裝 Guid，您可以排除一組 [Visual Studio 功能的封裝 Guid](../extensibility/package-guids-of-visual-studio-features.md)。  
  
## 。Pkgdef 檔案  
 .Pkgdef 檔可讓您定義應用程式安裝時所設定的應用程式的登錄項目。 .Pkgdef 檔的描述及使用 Visual Studio shell 的登錄項目清單，請參閱 [.Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
## 替代字串  
 中所列的.pkgdef 和.pkgundef 檔案中使用的替代字串 [替代字串中使用。Pkgdef 和。Pkgundef 檔案](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
## 其他設定  
 如果您的獨立的 shell 應用程式相依於 Microsoft.VisualStudio.GraphModel.dll，您需要獨立 Shell 應用程式的.config 檔案中加入下列繫結重新導向︰  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```