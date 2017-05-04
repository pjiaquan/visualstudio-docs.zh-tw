---
title: "文件層級自訂中的快取資料 | Microsoft Docs"
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
  - "快取資料 [Visual Studio 中的 Office 程式開發], 關於快取資料"
  - "資料 [Visual Studio 中的 Office 程式開發], 快取"
  - "資料 [Visual Studio 中的 Office 程式開發], 文件層級方案"
  - "資料快取 [Visual Studio 中的 Office 程式開發], 關於資料快取"
  - "資料島 [Visual Studio 中的 Office 程式開發]"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發], 資料模型"
  - "檢視 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 文件層級自訂中的快取資料
  文件層級自訂的主要目標之一就是在 Office 文件中將資料與檢視分開。  資料是指存放在文件中的資訊，包括數字和文字。  檢視則是指 Microsoft Office Word 和 Microsoft Office Excel 的使用者介面和物件模型。  
  
 Visual Studio 是以讓資料內嵌為「*資料島*」\(Data Island\)，也稱為「*資料快取*」\(Data Cache\) 的方式，在文件層級自訂中將資料與檢視分開。  您可以直接讀取或修改資料，而不用啟動 Word 或 Excel。  當您需要在未安裝 Microsoft Office 的伺服器上修改文件中的資料時，這種方法會很有用。  Word 和 Excel 主要用於用戶端環境，而非設計用來在伺服器上執行。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 如需文件層級自訂的詳細資訊，請參閱 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)和[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。  
  
## 了解快取資料程式設計模型  
 資料島可以包含方案中符合特定需求的任何物件。  這些物件包括 <xref:System.Data.DataSet> 物件、<xref:System.Data.DataTable> 物件，以及可以用 <xref:System.Xml.Serialization.XmlSerializer> 類別 \(Class\) 序列化的其他物件。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。  
  
 若要提供快取資料的檢視，您可以將 Windows Form 控制項和文件上的「*主控制項*」\(Host Control\) 繫結至資料島中的物件。  資料島與資料繫結控制項之間的資料繫結，可讓兩者保持同步。  您也可以將驗證程式碼加入與控制項無關的資料。  如需詳細資訊，請參閱[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 主控制項是 Excel 和 Word 物件模型中原生物件的擴充版本。  不像原生物件，主控制項可以直接繫結至 Managed 資料物件。  如需詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)與[Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
## 存取伺服器上的快取資料  
 若要存取文件中的快取資料，您可以使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別。  此類別是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的一部分，可以用在未執行 Excel 或 Word 的伺服器上。  當使用者在您修改快取資料之後開啟文件時，任何繫結至資料的控制項會自動與變更同步，使用者看到的會是更新的資料。  如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 在伺服器上寫入資料時，並不需要 Excel 和 Word；只有在用戶端上檢視時，才需要 Excel 和 Word。  甚至也不需要在伺服器上安裝 Excel 和 Word，  因此改善了延展性與功能，可以快速執行含資料島文件的批次處理。  
  
## 供離線使用的資料快取  
 將資料存放在資料島中就能在離線時使用。  使用者一開始開啟文件或從伺服器要求文件，資料島就會填滿最新的資料。  資料島已經快取在文件中，之後就可供離線使用。  使用者 \(和您的程式碼\) 雖然沒有即時連接可用，也可以操作資料。  當使用者再重新連接時，資料的變更就可以傳回到伺服器資料來源。  
  
## 快取資料和自訂 XML 組件的比較  
 自訂 XML 組件在 2007 Microsoft Office system 中引入，做為在文件中儲存任意 XML 片段的方式。  雖然自訂 XML 組件可以用在許多與資料快取相同的情節中，但是資料島與自訂 XML 組件之間還是有所不同。  如需自訂 XML 組件的詳細資訊，請參閱[自訂 XML 組件概觀](../vsto/custom-xml-parts-overview.md)。  
  
 下表列出一些相異和相似處。  
  
||資料快取|自訂 XML 組件|  
|-|----------|---------------|  
|哪些 Office 應用程式可以使用它們？|下列應用程式的文件層級自訂：<br /><br /> -   Excel<br />-   Word|下列應用程式的文件層級和應用程式層級方案：<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|您可以儲存哪些資料型別？|自訂組件 \(Assembly\) 中，任何符合特定需求的公用物件。  如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。|任何 XML 資料。|  
|您可以存取資料而不啟動 Microsoft Office 應用程式嗎？|可以，使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 提供的 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別即可。|可以，使用 <xref:System.IO.Packaging> 命名空間中的類別，或是使用 Open XML Format SDK 即可。|  
  
## 請參閱  
 [Office 方案的資料](../vsto/data-in-office-solutions.md)   
 [Office 方案在 Visual Studio 中的架構](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  