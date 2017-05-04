---
title: "如何：將資料庫的資料填入工作表 | Microsoft Docs"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 加入至工作表"
  - "資料庫 [Visual Studio 中的 Office 程式開發], 填入工作表"
  - "工作表 [Visual Studio 中的 Office 程式開發], 填入"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# 如何：將資料庫的資料填入工作表
  您可以存取資料文件層級 Office 方式預期您存取 Windows Form 專案中的資料。  您可以使用相同的工具和程式碼將資料帶入方案中，甚至可以使用 Windows Form 控制項顯示資料。  此外，您可以利用一種稱為主控制項的控制項，這是 Microsoft Office Excel 中的原生 \(Native\) 物件，但是經過事件和資料繫結 \(Data Binding\) 功能的加強。  如需詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 下列程式碼範例示範如何使用設計工具，將資料繫結控制項加入至文件層級專案。  如需如何在執行階段，將資料繫結控制項加入至應用程式層級專案的範例，請參閱[逐步解說：VSTO 增益集專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需觀看相關示範影片，請參閱[如何將資料轉送至 Excel 工作表？](http://go.microsoft.com/fwlink/?LinkID=130277)\(英文\) 和[如何在 Excel 中使用資料庫資料？](http://go.microsoft.com/fwlink/?LinkID=130287)\(英文\)。  
  
## 在設計階段將資料繫結控制項加入至工作表  
  
#### 若要用資料庫的資料填入工作表  
  
1.  在 Visual Studio 中開啟 Excel 文件層級專案，並在設計工具中開啟工作表。  
  
2.  開啟 \[**資料來源**\] 視窗，並建立專案的資料來源。  如需詳細資訊，請參閱[如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
3.  將您想要的欄位或資料表從 \[**資料來源**\] 視窗拖曳至工作表。  
  
 會在工作表上建立下列其中一種控制項：  
  
-   如果拖曳欄位，則會在工作表上建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  如需詳細資訊，請參閱[NamedRange 控制項](../vsto/namedrange-control.md)。  
  
-   如果拖曳資料表，則會在工作表上建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  如需詳細資訊，請參閱[ListObject 控制項](../vsto/listobject-control.md)。  
  
 您可以在 \[**資料來源**\] 視窗中選取資料表或欄位，然後從下拉式清單中選擇不同控制項，以加入不同的控制項。  
  
## 專案中的物件  
 除了控制項之外，下列資料相關物件也會自動加入至您的專案：  
  
-   具型別資料集，可封裝您透過資料庫連接的資料表。  如需詳細資訊，請參閱[使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   <xref:System.Windows.Forms.BindingSource>，可將控制項連接至具型別資料集。  如需詳細資訊，請參閱[BindingSource 元件概觀](../Topic/BindingSource%20Component%20Overview.md)。  
  
-   TableAdapter，可將具型別資料集連接至資料庫。  如需詳細資訊，請參閱[TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
-   TableAdapterManager，可用來協調資料集中的資料表配接器以啟用階層式更新。  如需詳細資訊，請參閱[階層式更新](../data-tools/hierarchical-update.md)與[TableAdapterManager 概觀](../Topic/TableAdapterManager%20Overview.md)。  
  
 當您執行專案時，控制項會顯示資料來源中的第一筆資料錄。  您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者可以捲動資料錄。  
  
#### 若要捲動資料錄  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，例如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 如需如何將更新傳送至具型別資料集和資料庫的詳細資訊，請參閱 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：將服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [如何:傳送資料至 Excel 工作表](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [如何:使用 Excel 中的資料庫資料?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  