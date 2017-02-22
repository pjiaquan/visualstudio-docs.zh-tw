---
title: "使用專案 Factory 建立專案 | Microsoft Docs"
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
  - "專案的處理站"
  - "專案 [Visual Studio SDK]，專案工廠"
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用專案 Factory 建立專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案中的型別[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用*專案工廠*來建立專案物件的執行個體。  專案工廠很類似 cocreatable 的 COM 物件的標準類別工廠的。  但是，並非 cocreatable 專案的物件: 只可以建立使用專案處理站。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會呼叫在使用者載入現有的專案，或建立新的專案中時，在您的 VSPackage 實作專案工廠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  新的專案物件提供 IDE，具有足夠的資訊來填入 \[方案總管\] 中。  新的專案物件也會提供所需的介面支援所有相關的 UI 動作啟動 ide。  
  
 您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>在專案中的類別中的介面。  一般而言，它會保留在自己的模組。  
  
 如需範例之實作的`IVsProjectFactory`介面資訊，請參閱位於的 PrjFac.cpp [Basic Project](http://msdn.microsoft.com/zh-tw/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)範例目錄。  
  
 正在進行彙總之由擁有者所支援的專案必須保存在其專案檔案的擁有者金鑰。  當<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>專案上呼叫方法以擁有者的金鑰、 附屬的專案將專案工廠 GUID 接著會呼叫它的擁有者識別碼`CreateProject`方法以執行實際建立此專案處理站。  
  
## 建立擁有的專案  
 在一位擁有人擁有的專案中建立兩個階段：  
  
1.  藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> 方法。  這可讓擁有的專案機會建立彙總的專案物件根據輸入的控制`IUnknown`。  擁有的專案通過內部`IUnknown`和彙總的物件傳回給擁有者的專案。  這會讓擁有的專案有機會來儲存內部`IUnknown`。  
  
2.  藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> 方法。  擁有的專案不會其所有的執行個體化，而非電話呼叫這個方法`IVsProjectFactory::CreateProject` ，就可能發生的情況為自己尚未擁有的專案。  輸入`VSOWNEDPROJECTOBJECT`列舉型別通常是彙總的附屬的專案。  擁有的專案可以使用這個變數，以判斷是否已建立其專案物件 \(cookie 不等於 NULL\) 或必須建立 \(cookie 等於 NULL\)。  
  
 唯一的專案 GUID，類似於 cocreatable 的 COM 物件的 CLSID 來識別專案類型。  一般而言，一個專案建立的單一專案類型、 執行個體，雖然您可以有一個專案工廠的工廠控點會處理多個專案類型的 GUID。  
  
 專案類型都與特定的副檔名相關聯。  當使用者嘗試開啟現有的專案檔案，或嘗試由複製的範本來建立新的專案時，則 IDE 會使用該檔案副檔名來判斷對應的專案 GUID。  
  
 IDE 會決定是否必須建立新的專案或開啟現有專案的特定型別，IDE 會使用中的資訊如 \[HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0\\Projects\] 找出哪一個 VSPackage 的系統登錄會實作必要的專案工廠。  IDE 載入此 VSPackage。  在<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>方法中，VSPackage 必須登錄其專案與 IDE 藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>方法。  
  
 主要的方法`IVsProjectFactory`介面是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>它應該處理兩個案例： 開啟現有的專案，並建立新的專案。  大部分的專案會將專案狀態儲存在專案檔中。  一般而言，新的專案由的製作一份範本檔傳遞至`CreateProject`方法，然後開啟 \[複本。  現有的專案會具現化藉由直接開啟專案檔傳遞至`CreateProject`方法。  `CreateProject`方法可依需要對使用者顯示額外的 UI 功能。  
  
 專案可以也不使用檔案，相反地，其專案狀態儲存在檔案系統，例如資料庫或 Web 伺服器以外的儲存機制。  如此一來，檔案名稱參數傳遞至`CreateProject`方法不是實際檔案系統路徑，而是唯一的字串 — URL，來識別專案資料。  您不需要複製範本檔案傳遞給`CreateProject`來觸發執行適當的建構序列。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)