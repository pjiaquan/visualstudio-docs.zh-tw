---
title: "移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Office 專案在執行前所必須進行的變更 | Microsoft Docs"
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
  - "Office 專案 [Visual Studio 中的 Office 程式開發], 移轉至 .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Office 專案在執行前所必須進行的變更
  如果 Office 專案的目標 Framework 從舊版的 .NET Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須執行下列工作，以確保解決方案可以在開發電腦和使用者電腦上執行：  
  
-   如果專案是從 Visual Studio 2008 升級，請移除專案中的 <xref:System.Security.SecurityTransparentAttribute>。  
  
-   在 Visual Studio 中執行 **Clean** 命令，能夠在開發電腦上執行或偵錯專案。  
  
-   更新專案的 .NET Framework 必要條件。  
  
-   如果在變更目標 Framework 之前已使用 ClickOnce 部署了解決方案，使用者也必須重新安裝解決方案。  
  
 如需這些工作每一項的詳細資訊，請參閱下列對應的章節。  
  
## 從由 Visual Studio 2008 升級的專案中移除 SecurityTransparent 屬性  
 如果 Office 專案從 Visual Studio 2008 升級，且專案的目標 Framework 隨後變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須從專案中移除 <xref:System.Security.SecurityTransparentAttribute>。 Visual Studio 不會為您自動移除這個屬性。 如果不移除這個屬性，您就會在編譯專案時收到錯誤訊息。  
  
 如需 Visual Studio 將已升級專案的目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的條件的詳細資訊，請參閱 [升級和移轉 Office 方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
#### 移除 SecurityTransparentAttribute  
  
1.  請使用在 Visual Studio 中開啟的專案，開啟 \[方案總管\]。  
  
2.  在 \[屬性\] 節點 \(C\#\) 或 \[我的專案\] 節點 \(Visual Basic\) 下，按兩下 AssemblyInfo 程式碼檔，以在程式碼編輯器中加以開啟。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，您必須按一下 \[方案總管\] 中的 \[顯示所有檔案\] 按鈕，才能查看 AssemblyInfo 程式碼檔。  
  
3.  找出 <xref:System.Security.SecurityTransparentAttribute>，並將它從檔案移除或加上註解。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## 執行清除命令以在開發電腦上偵錯或執行專案  
 如果在專案的目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本之前就已建立 Office 專案，您必須執行 \[清除\] 命令，然後在目標 Framework 變更之後重新建置專案。  如不執行 \[清除\] 命令，您會在嘗試偵錯或執行重定目標的專案時收到 <xref:System.Runtime.InteropServices.COMException>。  
  
 如需 \[清除\] 命令的詳細資訊，請參閱 [建置 Office 方案](../vsto/building-office-solutions.md)。  
  
## 更新部署的必要條件  
 當 Office 專案的目標重新設定為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本時，您也必須更新 \[必要條件\] 對話方塊中對應的 .NET Framework 先決條件。  否則 ClickOnce 部署或 InstallShield 限量版專案會查找並安裝舊版的 .NET Framework。  
  
 如需更新使用者電腦部署必要條件的詳細資訊，請參閱[HOW TO：在使用者電腦上安裝必要條件來執行 Office 方案](http://msdn.microsoft.com/zh-tw/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
## 在使用者電腦上重新安裝解決方案  
 如果您使用 ClickOnce 部署以 .NET Framework 3.5 為目標的 Office 解決方案，然後又將專案目標重定為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，則使用者必須解除安裝解決方案，並在您重新發行後再重新安裝解決方案。  如果您重新發行重定目標的解決方案，而使用者電腦上又更新了解決方案，則使用者會在執行更新的解決方案時收到 <xref:System.Runtime.InteropServices.COMException>。  
  
## 請參閱  
 [將 Office 方案移轉至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  