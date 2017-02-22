---
title: "專案持續性 | Microsoft Docs"
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
  - "持續性專案"
  - "專案 [Visual Studio SDK]，持續性"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 專案持續性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

持續性是主要的設計考量為您的專案。  大部分的專案使用代表檔匯入失敗的專案項目  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]也支援針對其中的資料是以非檔案基礎的專案。  必須保存這兩個專案和專案檔所擁有的檔案。  IDE 會指示，將本身或專案項目儲存專案。  
  
 專案範本會傳遞至專案的工廠。  範本應該支援所有專案項目，根據特定專案類型的需求來的初始化。  這些範本可以稍後儲存為專案檔和由透過方案 IDE。  如需詳細資訊，請參閱 [使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)和 [方案](../../extensibility/internals/solutions.md)。  
  
 專案項目可以是以檔案為基礎，或以非檔案為基礎：  
  
-   檔案為基礎的項目可以是本機或遠端。  在 C\# 中的 Web 專案，例如，連線到遠端系統上的檔案保存在本機上，而檔案本身保存遠端系統上。  
  
-   以檔案為基礎的項目可以將項目儲存到資料庫或儲存機制中。  
  
## 認可模型  
 決定專案項目位於何處，您必須選擇適當的認可模型。  比方說，具有本機檔案的檔案為基礎的模型，在每個專案可以儲存獨立。  在儲存機制的模型中，您可以儲存在一個交易中的多個項目。  如需詳細資訊，請參閱 [專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)。  
  
 如果要判斷檔案的副檔名，請實作專案<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面，可提供啟用物件的用戶端實作的資訊**另存新檔** \] 對話方塊中 — 也就是來填入**檔案類型**下拉式列示與管理初始檔案的副檔名。  
  
 IDE 呼叫`IPersistFileFormat`介面來表示專案應保存它的專案對專案項目適當地。  因此，物件會擁有其檔案和格式的所有層面。  這包括物件的格式名稱。  
  
 在項目不是檔案的情況下`IPersistFileFormat`仍是如何非檔案類型的項目會保存。  專案檔案，例如.vbp 檔，如[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案或.vcproj 檔案的[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案，也必須保存。  
  
 對於儲存動作，會在 IDE 測試執行的文件表格 \(RDT\) 和階層架構會傳遞至命令<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>介面。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>實作方法來判斷是否已修改的項目。  如果項目， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A>實作方法來儲存已修改的項目。  
  
 上的方法`IVsPersistHierarchyItem2`介面用來決定是否可以重新載入項目，如果項目可以是的若要重新載入它。  此外， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>可以實作方法，以使變更的項目，此時反而得丟棄但沒有進行儲存。  
  
## 請參閱  
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)