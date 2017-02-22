---
title: "VSPackage 所選擇的安裝目錄 | Microsoft Docs"
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
  - "VSPackages，安裝目錄"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# VSPackage 所選擇的安裝目錄
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 和其支援的檔案必須在使用者的檔案系統。  位置是根據是否 VSPackage 管理或不加以管理，您的並排顯示版本控制配置和使用者的選擇而定。  
  
## 未受管理的 VSPackages  
 未受管理的 VSPackage 是 COM 伺服器，可以安裝在任何位置。  它的註冊資訊必須能夠正確反映它的位置。  安裝程式使用者介面 \(UI\) 應該提供做為子目錄的 ProgramFilesFolder Windows Installer\] 屬性指定預設位置。  例如：  
  
 \[\] ProgramFilesFolderMyCompany\\MyVSPackageProduct\\V1.0\\  
  
 允許使用者變更預設目錄，以符合保留小的開機磁碟分割的使用者，並想要在另一個磁碟區上先安裝應用程式和工具。  
  
 如果您想要以並排配置使用已建立版本的 VSPackage，您可以使用來儲存不同版本的子目錄。  例如：  
  
 \[\] ProgramFilesFolderMyCompany\\MyVSPackageProduct\\V1.0\\2002\\  
  
 \[\] ProgramFilesFolderMyCompany\\MyVSPackageProduct\\V1.0\\2003\\  
  
 \[\] ProgramFilesFolderMyCompany\\MyVSPackageProduct\\V1.0\\2005\\  
  
## 受管理的 VSPackages  
 受管理的 VSPackages 也可以安裝在任何位置。  不過，您應考慮一律進行安裝至全域組件快取 \(GAC\) 中，以減少組件載入時間。  受管理的 VSPackages 永遠是強式名稱的組件，因為它們安裝在 GAC 中表示只有在安裝期間發生的其強式名稱簽章驗證。  安裝檔案系統中的其他地方的強式名稱組件必須確認每次載入它們的簽章。  當您安裝在 GAC 中的受管理的 VSPackages 時，使用 regpkg 工具的**\/assembly**參數寫入登錄項目指向組件的強式名稱。  
  
 如果您安裝受管理的 VSPackages 在 GAC 以外的其他位置時，請依照下列較早的建議給未受管理的 VSPackages，來選擇的目錄階層。  使用 regpkg 工具的**\/codebase**參數寫入登錄項目指向 VSPackage 組件的路徑。  
  
 如需詳細資訊，請參閱 [註冊和取消註冊 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)。  
  
## 附屬 Dll  
 依照慣例，VSPackage 附屬 Dll，其中包含特定的地區設定的資源，位於 VSPackage 目錄的子目錄中。  子目錄對應於地區設定識別碼 \(LCID\) 值。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)指出登錄項目控制在何處[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實際上會搜尋 VSPackage 的附屬 DLL。  不過， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]嘗試載入未依下列次序的 LCID 值命名的子目錄中的附屬 DLL：  
  
1.  預設 LCID \(VS LCID，例如 \\ 1033 英文\)  
  
2.  預設值與預設子語言 LCID。  
  
3.  系統預設的 LCID。  
  
4.  預設子語言與系統預設 LCID。  
  
5.  美式  英文 \(。  \\ 1033 或。  \\0x409\)。  
  
 如果您 VSPackage 的 DLL 中包含資源而 SatelliteDll\\DllName 登錄項目指向它時， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會嘗試依上述順序將它們載入。  
  
## 請參閱  
 [選擇 \[共用和版本建立 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [管理 Vspackage](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/zh-tw/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)