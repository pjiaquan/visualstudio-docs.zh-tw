---
title: "撰寫的 Windows Installer 封裝 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".msi 檔案 Vspackage"
  - "msi 檔案 Vspackage"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 撰寫的 Windows Installer 封裝
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

資料磁碟機的 Windows Installer 模型。 您不需要撰寫程序的指令碼，將檔案複製並寫入登錄項目，例如，您撰寫資料列和資料行包含檔案和登錄資料的資料庫資料表中。  
  
## 資料庫項目  
 若要安裝 VSPackage 時，Windows Installer 套件必須包含資料庫項目，以執行下列工作:  
  
-   搜尋系統以找出的版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 支援 \(使用 Windows Installer 資料表包含 AppSearch、 CompLocator、 RegLocator、 DrLocator，以及簽章\)。  
  
-   如果不支援的版本，請取消安裝 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 安裝或 \(使用 LaunchCondition 資料表\) 不符合 VSPackage 的其他系統需求。  
  
-   安裝 VSPackage 和相依檔案 \(使用目錄、 元件和檔案資料表\)。  
  
-   登錄 \(使用登錄資料表\) 中加入 VSPackage 的適當資訊。  
  
-   整合 VSPackage 中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 藉由呼叫 **devenv.exe \/setup** \(使用 CustomAction 資料表\)。  
  
 如需詳細資訊，請參閱 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)。  
  
## 安裝程式工具  
 許多協力廠商的安裝工具會提供 Windows Installer 封裝的開發環境。 兩個免費的工具如下所示:  
  
-   InstallShield 限量版  
  
     您可以透過 Visual Studio 取得 InstallShield 的限制的版本 **新的專案** \] 對話方塊。 展開 **其他專案類型** ，然後選取 **安裝和部署**。 選取 \[InstallShield 範本。  
  
-   Windows Installer XML Toolset  
  
     工具組會建置 XML 原始程式檔的 Windows Installer 套件。 工具組是 Microsoft 的開放原始碼專案。 您可以下載來源程式碼和可執行檔 [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix)。  
  
 適用於整合的商業產品 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], ，請參閱 [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/)。  
  
## 請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)