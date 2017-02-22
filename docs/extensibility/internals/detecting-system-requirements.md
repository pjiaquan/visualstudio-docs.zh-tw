---
title: "偵測系統需求 | Microsoft Docs"
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
  - "安裝程式, VSPackage"
  - "啟動條件"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
caps.handback.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
---
# 偵測系統需求
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 無法運作，除非已安裝 Visual Studio。 當您使用 Microsoft Windows Installer 來管理安裝 VSPackage 時，您可以設定來偵測是否已安裝 Visual Studio 安裝程式。 您也可以設定它來檢查系統有其他需求，例如，特定版本的 Windows 或特定的 RAM 數量。  
  
## 偵測 Visual Studio 版本  
 若要判斷是否已安裝的 Visual Studio 版本中，確認安裝登錄機碼的值 \(REG\_DWORD\) 1 中適當的資料夾，如下列表格所列。 請注意，Visual Studio 版本的階層架構︰  
  
1.  企業  
  
2.  Professional  
  
3.  社群  
  
 安裝 「 高 」 的版本時，會加入該版本以及與 「 低 」 版本的登錄機碼。 也就是如果 Enterprise edition 已安裝，安裝金鑰設為 1 的 Enterprise、 以及專業人員和社群版本。 因此，您必須只會檢查您所需要的 「 高 」 版本。  
  
> [!NOTE]
>  在登錄編輯程式的 64 位元版本中，32 位元的金鑰會顯示在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\ 底下。 Visual Studio 金鑰受到 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\。  
  
|產品|Key|  
|--------|---------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell （整合和獨立模式）|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Visual Studio 執行偵測  
 如果您安裝 VSPackage 時，正在執行 Visual Studio 將無法正確註冊 VSPackage。 安裝程式必須偵測何時執行 Visual Studio，並拒絕安裝程式。 Windows Installer 不讓您啟用這類偵測使用資料表項目。 相反地，您必須建立自訂動作，如下所示︰ 使用 `EnumProcesses` 函式來偵測的 devenv.exe 處理序，並請將安裝程式屬性，可在啟動條件或有條件地顯示對話方塊，提示使用者關閉 Visual Studio。  
  
## 請參閱  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)