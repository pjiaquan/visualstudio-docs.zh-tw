---
title: "文件層級自訂中的 XML 結構描述和資料 | Microsoft Docs"
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
  - "Visual Studio 中的 Office 程式開發, XML"
  - "結構描述 [Visual Studio 中的 Office 程式開發]"
  - "XML [Visual Studio 中的 Office 程式開發], XML 結構描述"
  - "XML 結構描述 [Visual Studio 中的 Office 程式開發]"
  - "XML 結構描述 [Visual Studio 中的 Office 程式開發], 關於 XML 結構描述與資料"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 文件層級自訂中的 XML 結構描述和資料
  在**重要** 有關 Microsoft Word 的本主題開頭的資訊位於美國境外及其疆土或者使用對個人的優點和使用完整呈現和組織，或者執行中開發程式，由在選取範圍從之前的 Microsoft 授權之 Microsoft Word 產品，，當 Microsoft 從 Microsoft Word 移除特定功能的實作與自訂 XML 相關。  這些有關 Microsoft Word 的資訊不得供位於美國或其行政區以內，使用 Microsoft 在 2010 年 1 月 10 日以後所授權之 Microsoft Word 產品或開發適用程式之個人或組織閱讀或使用。凡是在該日期以前授權或是針對在美國地區以外使用所購買並授權的這些產品，其行為將有所不同。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel 和 Microsoft Office Word 提供將結構描述對應至文件的功能。  這項功能可以簡化將 XML 資料匯入文件，以及從文件匯出 XML 資料。  
  
 Visual Studio 會公開文件層級自訂中對應的結構描述項目，做為程式設計模型中的控制項。  如果是 Excel，Visual Studio 可支援將控制項繫結至資料庫、Web 服務和物件中的資料。  如果是 Word 和 Excel，Visual Studio 可支援執行窗格，其可與結構描述對應的文件搭配使用，以為方案建立加強的使用者經驗。  如需詳細資訊，請參閱[執行窗格概觀](../vsto/actions-pane-overview.md)。  
  
> [!NOTE]  
>  您不能在 Excel 方案中使用多重 XML 結構描述。  
  
## 結構描述附加至 Excel 活頁簿時所建立的物件  
 當您將結構描述附加至活頁簿時，Visual Studio 會自動建立多個物件並將這些物件加入至專案。  不應使用 Visual Studio 工具刪除這些物件，因為它們是由 Excel 進行管理。  若要刪除它們，請移除工作表中的對應項目，或使用 Excel 工具中斷與結構描述的連結。  
  
 主要物件有兩個：  
  
-   XML 結構描述 \(XSD 檔\)。  對於活頁簿中的每個結構描述，Visual Studio 都會將結構描述加入專案。  它會在 \[**方案總管**\] 中顯示為具有 XSD 擴充的專案項目。  
  
-   具型別的 <xref:System.Data.DataSet> 類別。  這個類別是根據結構描述建立的。  在 \[**類別檢視**\] 中可以看見這個資料集類別。  
  
## 當結構描述項目對應至 Excel 工作表時所建立的物件  
 當您從 \[**XML 原始檔**\] 工作窗格將結構描述項目對應至工作表時，Visual Studio 就會自動建立多個物件並將這些物件加入至專案：  
  
-   控制項。  程式撰寫模型中會針對活頁簿中的每個對應物件各建立一個 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項 \(如果是非重複的結構描述項目\) 或 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項 \(如果是重複的結構描述項目\)。  只有刪除活頁簿中的對應和對應物件，才能刪除 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  如需控制項的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
-   BindingSource。  當您將非重複的結構描述項目對應至工作表，藉以建立 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 時，就會一併建立 <xref:System.Windows.Forms.BindingSource> 而且 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項會繫結至 <xref:System.Windows.Forms.BindingSource>。  您必須將 <xref:System.Windows.Forms.BindingSource> 繫結至與對應至文件之結構描述相符的資料來源執行個體，例如建立的具型別 <xref:System.Data.DataSet> 類別執行個體。  您可以設定 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性 \(公開於 \[**屬性**\] 視窗中\)，藉以建立繫結。  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> 並不會針對 <xref:Microsoft.Office.Tools.Excel.ListObject> 物件建立。  您必須設定 \[**屬性**\] 視窗中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性，以手動方式將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至資料來源。  
  
### Office 對應結構描述和 Visual Studio 資料來源視窗  
 Office 的對應結構描述功能和 Visual Studio \[**資料來源**\] 視窗，都可以幫助您在 Excel 工作表上顯示資料，以進行報告或編輯。  在這兩種情況下，您都可以將資料項目拖曳至 Excel 工作表。  這兩種方法都會建立控制項，這些控制項是透過 <xref:System.Windows.Forms.BindingSource> 繫結至資料來源 \(例如 <xref:System.Data.DataSet> 或 Web 服務\) 的資料。  
  
> [!NOTE]  
>  當您將重複的結構描述項目對應至工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.ListObject>。  不過，<xref:Microsoft.Office.Tools.Excel.ListObject> 並不會透過 <xref:System.Windows.Forms.BindingSource> 自動繫結至資料。  您必須設定 \[**屬性**\] 視窗中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性，以手動方式將 <xref:Microsoft.Office.Tools.Excel.ListObject> 繫結至資料來源。  
  
 下表顯示這兩種方法之間的一些差異。  
  
|XML 結構描述|資料來源視窗|  
|--------------|------------|  
|使用 Office 介面。|使用 Visual Studio 中的 \[**資料來源**\] 視窗。|  
|啟用內建 Office 功能，以從 XML 檔匯入和匯出資料。|您必須以程式設計的方式提供匯入和匯出功能。|  
|您必須撰寫程式碼，才能用資料填滿產生的控制項。|從 \[**資料來源**\] 視窗加入的控制項會自動產生程式碼，以對其進行填滿，同時還包括您使用資料庫伺服器時的必要連接字串。|  
  
## 結構描述附加至 Word 文件的行為  
 將結構描述附加至文件層級 Office 專案中使用的 Word 文件時，不會建立資料物件。  不過，將結構描述項目對應至文件時，會建立控制項。  控制項的型別取決於您所對應的項目型別，重複項目會產生 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項，而非重複項目會產生 <xref:Microsoft.Office.Tools.Word.XMLNode> 控制項。  如需詳細資訊，請參閱[XMLNodes 控制項](../vsto/xmlnodes-control.md)與[XMLNode 控制項](../vsto/xmlnode-control.md)。  
  
## 包括 XML 結構描述之方案的部署  
 您應建立安裝程式，以部署使用對應至文件之 XML 結構描述的方案。  該安裝程式應在使用者電腦上的結構描述程式庫中註冊結構描述。  如果您不註冊結構描述，則方案仍會運作，因為 Word 會在使用者開啟文件時，根據文件中的項目產生暫存結構描述。  不過，使用者將無法對用於建立專案的結構描述進行驗證，也無法儲存該結構描述。  如需安裝程式的詳細資訊，請參閱[部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。  
  
 您也可將程式碼加入至專案，以檢查結構描述是否位於程式庫，以及和是否已註冊。  如果不是，則可以警告使用者。  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## 請參閱  
 [如何：在 Visual Studio 內將結構描述對應至 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [如何：在 Visual Studio 內將結構描述對應至工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  