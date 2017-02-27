---
title: "自訂工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages，自訂工具"
  - "工具 [Visual Studio] 自訂"
  - "自訂工具"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 自訂工具
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*自訂工具*可讓您與專案中的項目產生關聯的工具，並執行該工具，每次您儲存檔案。  特定自訂的工具，有時稱為*單一檔案產生器*，經常用來執行產生的資料，或進行相反動作的程式碼的轉譯器。  例如，單一檔案產生器建立[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]出.settings 和.resx 檔的原始程式碼。  產生的原始程式碼提供強型別存取.settings 和.resx 檔案中的資料。  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型都支援自訂工具。  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案類型並不需要。  您自己的專案型別也可以支援自訂工具。  
  
 自訂工具所實作的已註冊的元件`IVsSingleFileGenerator`介面。  
  
 自訂工具與其`ProjectItem`介面物件，而且就像設計工具和編輯器。  自訂工具會所代表的檔案`ProjectItem`為輸入，並將新的檔案，其檔名由`DefaultExtension`方法。  
  
## 在本節中  
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)  
 說明如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面，以實作自訂的工具。  
  
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)  
 說明如何判斷正確的命名空間，根據所使用的語言。  
  
 [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)  
 提供自訂工具的描述，讓所有登錄項目。  
  
 [公開型別，以視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 說明如何專案系統提供的支援視覺化設計工具產生的存取類別和型別來透過暫時的可移植執行檔 \(PE\) 的檔案。  
  
 [保存專案項目屬性](../../extensibility/persisting-the-property-of-a-project-item.md)  
 示範如何將保存的專案項目屬性，例如原始程式檔，在專案檔中的作者。  
  
## 參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 提供有關的詳細資訊， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>，這會將單一的輸入的檔轉換為可以編譯，或加入至專案的單一輸出檔案。  
  
 <xref:EnvDTE.ProjectItem>  
 說明`ProjectItem`介面，這表示專案中的項目。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 提供有關的詳細資訊， `DefaultExtension`方法會擷取指定給 \[輸出檔名的副檔名。  
  
## 相關章節  
 [擴充專案](../../extensibility/extending-projects.md)  
 說明如何使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案及方案能夠組織程式碼檔和資源檔，以及如何實作原始檔控制。