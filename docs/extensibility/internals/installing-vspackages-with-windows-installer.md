---
title: "使用 Windows Installer 安裝 Vspackage | Microsoft Docs"
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
  - "使用 Windows Installer 安裝 [Visual Studio SDK]，"
  - "VSPackages 部署"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用 Windows Installer 安裝 Vspackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

整合到您 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]需要不只將檔案複製到使用者的電腦。  您的 VSPackage 安裝程式必須安裝 VSPackage 和其相依的檔案，並要註冊並且將它們整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  您的 VSPackage 可以利用整合功能，例如顯示圖示，在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] splash 畫面和 \[關於\] 對話方塊。  
  
 Microsoft Windows Installer 檔案的建議方式是將分送您的 VSPackages。  簡單好用的 Windows 安裝程式套件可以在支援的任何 Windows 作業系統上執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  如需詳細資訊，請參閱 [Windows Installer](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
## 在本節中  
 [Windows 安裝程式的基本概念](../../extensibility/internals/windows-installer-basics.md)  
 提供 Windows 安裝程式的概觀。  
  
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)  
 將告訴您不同的方式，可支援並排顯示安裝這兩個程式的 VSPackages 和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [撰寫的 Windows Installer 封裝](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 提供的安裝程式遵循正確安裝，並整合到 VSPackages 的典型步驟概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [偵測系統需求](../../extensibility/internals/detecting-system-requirements.md)  
 說明如何安裝程式可以偵測到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]和它的元件和 \[取消\] 安裝程式如果不符合 VSPackage 的需求。  
  
 [管理元件](../../extensibility/internals/component-management.md)  
 討論如何開發 \[安裝程式，將會維護舊版產品的完整性。  
  
 [VSPackage 所選擇的安裝目錄](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 彙總選項可用於尋找 VSPackages。  
  
 [VSPackage 註冊](../../extensibility/internals/vspackage-registration.md)  
 將告訴您如何在安裝期間登錄 VSPackages 與自我登錄的原因是個好主意。  
  
 [部署專案類型](../../extensibility/internals/deploying-project-types.md)  
 討論如何使用新的專案類型彙總為 managed 程式碼的專案類型。  
  
 [如何: 產生安裝程式的登錄資訊](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 說明如何使用 RegPkg.exe 來產生註冊資訊清單的受管理的 VSPackage。  
  
 [必須在安裝後執行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 說明如何執行安裝後期的命令，以整合成 VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [解除安裝 Windows Installer VSPackage](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 說明當使用者解除安裝您的 VSPackage 時，您的安裝程式必須執行的步驟。  
  
## 相關章節  
 [安裝 VSPackage](../../misc/installing-vspackages.md)  
 討論如何建立並安裝 VSPackages，以及如何支援執行多個版本的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]一次。