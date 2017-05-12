---
title: "存取伺服器文件中的資料"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 在伺服器上存取"
  - "資料存取 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# 存取伺服器文件中的資料
  您可以對文件層級自訂中的資料進行程式設計，而不需使用 Microsoft Office Word 或 Microsoft Office Excel 的物件模型。  這表示您可以在未安裝 Word 或 Excel 的伺服器存取文件中內含的資料。  例如，伺服器上的程式碼 \(例如，在 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 頁面中\) 可以自訂文件中的資料，並將自訂的文件傳送給使用者。  當使用者開啟文件時，方案組件中的資料繫結 \(Data Binding\) 程式碼會將自訂的資料繫結至文件。  這是因為文件中的資料與使用者介面分離的結果。  如需詳細資訊，請參閱[文件層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 快取在伺服器上使用的資料  
 若要快取文件中的資料物件，請在設計階段使用 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性加以標示，或在執行階段使用主項目的 `StartCaching` 方法。  在文件中快取資料物件時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會將物件序列化至儲存在文件中的 XML 字串。  要快取的物件必須符合特定需求。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
 伺服器端程式碼可以操作資料快取中的任何資料物件。  繫結至快取資料執行個體的控制項會與使用者介面進行同步處理，因此對資料所做的任何伺服器端變更，會在文件於用戶端開啟時自動顯示。  
  
## 存取快取中的資料  
 您可以從 Office 以外的應用程式存取快取中的資料，例如，從主控台應用程式、Windows Form 應用程式或 Web 網頁。  存取快取資料的應用程式必須具有完全信任的權限，具有部分信任的 Web 應用程式無法插入、擷取或變更在 Office 文件中快取的資料。  
  
 資料快取可透過 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別之 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性所公開 \(Expose\) 的集合階層架構存取：  
  
-   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性 \(Property\) 會傳回 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>，其中包含文件層級自訂中的所有快取資料。  
  
-   每個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> 都會包含一個或多個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 物件。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 含有單一類別中定義的所有快取資料物件。  
  
-   每個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> 都會包含一個或多個 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 物件。  <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 代表單一快取資料物件。  
  
 下列程式碼範例會示範如何存取 Excel 活頁簿專案之 `Sheet1` 類別中的快取字串。  這個範例是 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 方法完整範例的一部分。  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## 修改快取中的資料  
 若要修改快取資料物件，通常可以執行下列步驟：  
  
1.  將快取物件的 XML 表示還原序列化為物件的新執行個體。  您可以使用表示快取資料物件之 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 的 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 屬性來存取 XML。  
  
2.  對此複本進行變更。  
  
3.  使用下列其中一個選項，將已變更的物件序列化為資料快取：  
  
    -   若要自動序列化變更，請使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法。  這個方法會使用 **DiffGram** 格式，以便序列化資料快取中的 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 和具型別資料集物件。  **DiffGram** 格式會確保對離線文件之資料快取所進行的變更會正確地傳送至伺服器。  
  
    -   如果要執行自己所偏好的序列化，將變更修改到快取的資料，您可以直接寫入至 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> 屬性。  如果您使用 <xref:System.Data.Common.DataAdapter> 將 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或具型別資料集中的資料變更更新至資料庫，請指定 **DiffGram** 格式。  否則，<xref:System.Data.Common.DataAdapter> 將會以加入新資料列而非修改現有資料列的方式更新資料庫。  
  
### 修改資料但不還原序列化目前的値  
 在某些情況下，您可能不先還原序列化快取物件目前的値，就要修改其値。  例如，您要變更簡單型別物件的値 \(例如字串或整數\)，或是您要初始化伺服器上文件中快取的 <xref:System.Data.DataSet>。  在這些情況下，您可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> 方法，而不需先還原序列化快取物件目前的値。  
  
 下列程式碼範例會示範如何變更 Excel 活頁簿專案之 `Sheet1` 類別中的快取字串值。  這個範例是 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> 方法完整範例的一部分。  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### 修改資料快取中的 Null 值  
 當儲存並關閉文件時，資料快取不會儲存具有 **null** 值的物件。  當您修改快取資料時，這個限制會造成下列數個結果：  
  
-   如果您將資料快取中的任何物件設定為 **null** 値，當開啟文件時，資料快取中的所有物件都會自動設定為 **null**，而且當儲存並關閉文件時，整個資料快取都會遭到清除。  也就是說，所有快取物件都會從資料快取中移除，而且 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 集合將是空集合。  
  
-   如果您使用資料快取中的 **null** 物件來建置方案時，而且要在第一次開啟文件之前使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別來初始化這些物件，則必須確定您會初始化資料快取中的所有物件。  如果只初始化部分物件，當開啟文件時，所有物件都會自動設定為 **null**，而且當儲存並關閉文件時，整個資料快取都會遭到清除。  
  
## 存取快取中的具型別資料集  
 如果您想要同時從 Office 方案和 Office 以外的應用程式 \(例如 Windows Form 應用程式或 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 專案\) 存取具型別資料集中的資料，則必須在兩個專案中參考的另一個組件中定義具型別資料集。  如果您使用 \[**資料來源組態精靈**\] 或 \[**DataSet 設計工具**\] 將具型別資料集加入至每個專案，.NET Framework 就會將兩個專案內的具型別資料集視為不同的型別。  如需建立具型別資料集的詳細資訊，請參閱 [如何：建立具類型資料集](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md)。  
  
## 請參閱  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [文件層級自訂中的快取資料](../vsto/cached-data-in-document-level-customizations.md)  
  
  