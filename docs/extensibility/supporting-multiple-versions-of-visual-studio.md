---
title: "支援多個版本的 Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 中，支援多個版本"
  - "VSPackages，-並存相容性"
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 支援多個版本的 Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個詞彙 *\-並存* 表示您可以安裝與維護多個版本的同一部電腦上的產品。 VSPackages，這表示使用者可以擁有相同的電腦上安裝的數個 Visual Studio 版本。 不過，您不能有單一版本的 Visual Studio 將載入您 VSPackages\-並存版本。  
  
 無法載入的並存版本的 Visual Studio VSPackage 之前，請考慮下列各項:  
  
-   您必須決定您想要遵循的並行的實作策略。  
  
     如需詳細資訊，請參閱[選擇 \[共用和版本建立 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)。  
  
-   您的方案和專案檔案的格式必須符合您的實作策略。  
  
     如需詳細資訊，請參閱 [升級自訂專案](../misc/upgrading-custom-projects.md) 與 [註冊副檔名的並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)。  
  
-   您的安裝程式必須處理實作策略，以便建立版本的元件，以及所有的版本之間共用的元件正確安裝及註冊。  
  
     如需詳細資訊，請參閱 [使用 Windows Installer 安裝 Vspackage](../extensibility/internals/installing-vspackages-with-windows-installer.md) 以及 [管理元件](../extensibility/internals/component-management.md)。  
  
    > [!NOTE]
    >  安裝 Visual Studio 的版本也會安裝對應的版本 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 例如，在同一部電腦上安裝 Visual Studio 2010 和 Visual Studio 2012 也會安裝 4.0 和 4.5 版 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], 分別。  
  
## 在本節中  
 [選擇 \[共用和版本建立 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 說明如何解決在 VSPackage 中的由並行問題。  
  
 [註冊副檔名的並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 描述如何 VSPackage 時，可以並存的案例中註冊檔案關聯。  
  
## 相關章節  
 [安裝 VSPackage](../misc/installing-vspackages.md)  
 討論如何建置和安裝 VSPackages，以及如何支援同時執行多個版本的 Visual Studio 的使用者。