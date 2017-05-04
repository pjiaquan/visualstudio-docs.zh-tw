---
title: "如何：快取資料供離線使用或於伺服器上使用 | Microsoft Docs"
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
  - "資料快取 [Visual Studio 中的 Office 程式開發], 離線使用"
  - "資料快取 [Visual Studio 中的 Office 程式開發], 伺服器使用"
  - "資料集 [Visual Studio 中的 Office 程式開發], 快取"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發], 資料"
  - "離線資料 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# 如何：快取資料供離線使用或於伺服器上使用
  您可以將文件中的資料項目標示為快取，使其可以在離線時使用。  而在文件存放在伺服器上時，這也可以讓其他的程式碼操作文件中的資料。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您可以在程式碼中宣告資料項目，或是當使用 <xref:System.Data.DataSet> 時，藉由在 \[**屬性**\] 視窗中設定屬性，將資料項目標示為快取。  如果您要快取不是 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 的資料項目，請確認此項目符合在文件中快取的準則。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
> [!NOTE]  
>  使用 Visual Basic 建立且標記為 **Cached** 和 **WithEvents** 的資料集 \(包括從 \[**資料來源**\] 視窗或 \[**工具箱**\] 拖曳且將 \[**CacheInDocument**\] 屬性設定為 \[**True**\] 的資料集\) 會在快取中其名稱前加上底線。  例如，如果建立資料集並將其命名為 Customers，<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 在快取中的名稱將會是 \_Customers。  當您使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 存取此快取項目時，必須指定 \_Customers 而不是 Customers。  
  
### 若要使用程式碼快取文件中的資料  
  
1.  將資料項目的公用欄位或屬性宣告為專案中主項目類別的成員，例如 Word 專案中的 `ThisDocumen`t 類別或 Excel 專案中的 `ThisWorkbook` 類別。  
  
2.  將 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性 \(Attribute\) 套用至成員，以標示要儲存在文件資料快取中的資料項目。  下列程式碼範例會將這個屬性套用至 <xref:System.Data.DataSet> 的欄位宣告。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  加入程式碼以建立資料項目的執行個體，以及在可能情況下將其從資料庫載入。  
  
     資料項目只會在第一次建立時載入，此後快取會隨同文件保留，而您必須撰寫其他的程式碼來更新它。  
  
### 若要使用屬性視窗快取文件中的資料集  
  
1.  使用 Visual Studio 設計工具中的工具，將資料集加入至專案，例如使用 \[**資料來源**\] 視窗，將資料來源加入至專案。  
  
2.  如果沒有資料集的執行個體，請建立一個，並在設計工具中選取該執行個體。  
  
3.  在 \[**屬性**\] 視窗中，將 \[**CacheInDocument**\] 屬性設定為 \[**True**\]。  
  
     如需詳細資訊，請參閱[Office 專案中的屬性](../vsto/properties-in-office-projects.md)。  
  
4.  在 \[**屬性**\] 視窗中，將 \[**Modifiers**\] 屬性設定為 \[**Public**\] \(預設為 \[**Internal**\]\)。  
  
## 請參閱  
 [快取資料](../vsto/caching-data.md)   
 [如何：以程式設計方式快取 Office 文件的資料來源](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [如何：快取受密碼保護文件中的資料](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)   
 [儲存資料](../data-tools/saving-data.md)  
  
  