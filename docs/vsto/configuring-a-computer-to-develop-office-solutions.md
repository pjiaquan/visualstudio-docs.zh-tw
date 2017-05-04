---
title: "設定電腦以開發 Office 方案 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 Office 程式開發，安裝工具"
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: 97
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# 設定電腦以開發 Office 方案
  若要為 Microsoft Office 建立 VSTO 增益集和自訂，請安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本。  
  
|軟體|支援的版本|  
|--------|-----------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)] **Important:**  您必須在安裝期間選取 \[Microsoft Office Developer Tools\] 核取方塊。|  
|.NET Framework|-   .NET Framework 4 或更新版本。|  
|Microsoft Office|<ul><li>任何 Office 套件版本，包括 Office Professional Plus for Office 365。</li><li>下列任何一種獨立應用程式：<br /><br /> <ul><li>Excel</li><li>InfoPath \(僅限 Office 2013 和 Office 2010\)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> 必須在安裝 Office 時安裝 Visual Basic for Applications \(VBA\)。 **Important:**  不支援隨選即用版本的 Office 2010 應用程式。|  
  
 如需詳細的安裝步驟，請參閱[如何：設定電腦來開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)。  
  
## 如果專案範本未顯示或無法在 Visual Studio 中使用  
 如果安裝支援的 Visual Studio、.NET Framework 和 Microsoft Office 版本，但 Office 專案範本未顯示在 Visual Studio 的 \[新增專案\] 對話方塊中，或者在使用時出現錯誤，請檢查下列各項：  
  
-   確定電腦上已安裝 Microsoft Office 開發人員工具。  
  
     Office 開發人員工具是 Visual Studio 的選用元件，但通常會隨著 Visual Studio 自動安裝。 如果您透過指定要安裝的功能來自訂 Visual Studio 安裝，請確定已在安裝期間選擇 \[Microsoft Office Developer Tools\]，以安裝這些工具。  
  
     若要確定是否已安裝這些工具，請啟動 Visual Studio 安裝程式，並選擇 \[修改\] 按鈕。 選取 \[Microsoft Office Developer Tools\] 核取方塊，然後選擇 \[更新\] 按鈕。  
  
-   請確定您執行的 Office 版本不是隨選即用版本。 請參閱[如何：驗證電腦上的 Outlook 是否為隨選即用應用程式](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx)。  
  
-   確定只執行一個版本的 Microsoft Office。  
  
 如果持續發生問題，請參閱 [Office 方案錯誤的其他支援](../vsto/additional-support-for-errors-in-office-solutions.md)。  
  
## 請參閱  
 [使用者入門 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [如何：設定電腦來開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何：安裝 Visual Studio Tools for Office Runtime 可轉散發套件](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [如何：安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)  
  
  