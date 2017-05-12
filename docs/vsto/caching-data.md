---
title: "快取資料"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 快取"
  - "資料快取 [Visual Studio 中的 Office 程式開發]"
  - "資料快取 [Visual Studio 中的 Office 程式開發], 關於快取資料"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 快取資料
  您可以用文件層級自訂來快取資料物件，如此就可以在離線時，或是在不開啟 Microsoft Office Word 或 Microsoft Office Excel 的情況下存取資料。  若要快取物件，該物件必須具有符合特定需求的資料型別。  .NET Framework 中的許多通用資料型別都符合這些需求，包括 <xref:System.String>、<xref:System.Data.DataSet> 和 <xref:System.Data.DataTable>。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有兩種方法可以將物件加入至資料快取：  
  
-   若要在建置方案時將物件加入至資料快取，請將 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性 \(Attribute\) 套用至物件宣告。  如需詳細資訊，請參閱[如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。  
  
-   若要以程式設計的方式，在執行階段將物件加入至資料快取，請使用主項目 \(例如 `ThisDocument` 或 `ThisWorkbook` 類別\) 的 `StartCaching` 方法。  如需詳細資訊，請參閱[如何：以程式設計方式快取 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)。  
  
 將物件加入至資料快取後，您就可以存取並修改該快取資料，而不需啟動 Word 或 Excel。  如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## 要快取之資料物件的要求  
 若要快取方案中的資料物件，該物件必須符合下列需求：  
  
-   為主項目的讀寫公用 \(Public\) 欄位或屬性 \(如 `ThisDocument` 或 `ThisWorkbook` 類別\)。  
  
-   不是索引子或其他參數型屬性。  
  
 此外，資料物件必須透過 <xref:System.Xml.Serialization.XmlSerializer> 類別序列化，這表示物件的類型必須具有下列特性：  
  
-   是公用型別。  
  
-   具有無參數的公用建構函式。  
  
-   不執行要求其他安全性權限的程式碼。  
  
-   只公開可讀寫的公用屬性 \(忽略其他屬性\)。  
  
-   不公開多維式陣列 \(接受巢狀陣列\)。  
  
-   不從屬性和欄位傳回介面。  
  
-   不實作 <xref:System.Collections.IDictionary> \(如果是集合的話\)。  
  
 當您快取資料物件時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將物件序列化為 XML 字串，該字串儲存於文件的「*自訂 XML 組件*」\(Custom XML Part\) 中。  如需詳細資訊，請參閱[自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
## 快取的資料大小限制  
 對於您可以加入至文件中資料快取的資料總數，以及資料快取中任何個別物件的大小會有一些限制。  如果超過這些限制，應用程式可能會在資料儲存到資料快取時意外關閉。  
  
 若要避免這些限制，請遵循下列方針︰  
  
-   請勿將大於 10 MB 的任何物件加入至資料快取。  
  
-   請勿將超過 100 MB 的總資料量加入至單一文件的資料快取。  
  
 這些都是約略值。  確切的限制會根據數項因素而定，包括可用的 RAM 和執行中的處理序數目。  
  
## 控制快取物件的行為  
 若要進一步控制快取物件的行為，您可以在該快取物件的型別上實作 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 介面。  例如，如果要控制在物件被變更後如何告知使用者，則可實作這個介面。  如需示範如何實作 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 的程式碼範例，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中＜Excel 動態控制項範例＞和＜Word 動態控制項範例＞的 `ControlCollection` 類別。  
  
## 保存快取受密碼保護文件中資料的變更  
 如果您快取受密碼保護之文件中的資料物件，則不會儲存快取資料的變更。  您可以藉由覆寫兩個方法將變更儲存至快取資料。  請覆寫這些方法，以便在儲存文件時暫時移除保護，然後在儲存作業完成時重新套用保護。  
  
 如需詳細資訊，請參閱[如何：快取受密碼保護文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)。  
  
## 避免將 Null 值加入至資料快取時發生資料遺失  
 將物件加入至資料快取時，您必須先將所有快取物件初始化為非 **null** 值，才能儲存和關閉文件。  當儲存和關閉文件時，如果有任何快取物件擁有 **null** 值，則 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 將自動從資料快取移除所有快取物件。  
  
 如果在設計階使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性 \(Attribute\) 將含有 **null** 值的物件加入至資料快取，您就可以在開啟文件之前使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>類別來初始化快取資料物件。  如果您想要在使用者開啟文件之前初始化未安裝 Word 或 Excel 之伺服器上的快取資料，這個方法就很有用。  如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
## 請參閱  
 [如何：快取資料供離線使用或於伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [如何：以程式設計方式快取 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何：快取受密碼保護文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [逐步解說：使用快取資料集來建立主從式關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  