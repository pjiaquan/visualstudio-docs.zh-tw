---
title: "如何：將資料庫的資料填入文件"
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
  - "資料, 加入至文件"
  - "文件, 填入資料"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 如何：將資料庫的資料填入文件
  您可以用存取 Windows Form 專案資料的相同方式，存取 Microsoft Office 文件層級專案的資料。  使用相同的工具和程式碼，可從資料庫將資料帶入您的解決方案，而且可以使用 Windows Form 控制項顯示資料。  
  
 此外，也可以使用主控制項來顯示資料。  主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。  如需詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。  如需如何在執行階段於 VSTO 增益集專案中加入資料繫結控制項的範例，請參閱[逐步解說：VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關的影片示範，請參閱[使用 Visual Studio Tools for Office System \(3.0\) 將資料繫結至 Word 2007 內容控制項](http://go.microsoft.com/fwlink/?LinkId=136785)。  
  
## 在設計階段將控制項加入文件  
  
#### 以資料庫的資料填入文件  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟 Word 文件層級專案，同時在設計工具中開啟文件。  
  
2.  開啟 \[資料來源\] 視窗，並從資料庫建立資料來源。  如需詳細資訊，請參閱[如何：連接至資料庫中的資料](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
3.  將想要的欄位從 \[資料來源\] 視窗拖曳至您的文件。  
  
 內容控制項已加入文件。  內容控制項的類型取決於您選取的欄位資料類型。  如需詳細資訊，請參閱[內容控制項](../vsto/content-controls.md)。  
  
 您可以在 \[資料來源\] 視窗中選取資料欄位，藉此加入不同的控制項，再從下拉式清單中選擇不同的控制項。  
  
## 專案中的物件  
 除了控制項之外，下列與資料相關的物件會自動加入專案：  
  
-   封裝連接到資料庫之資料表的具類型資料集。  如需詳細資訊，請參閱 [使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。  如需詳細資訊，請參閱 [BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)。  
  
-   將具類型資料集連接至資料庫的 TableAdapter。  如需詳細資訊，請參閱 [TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
-   TableAdapterManager 用於協調資料集中的表格配接器，以啟用階層式更新。  如需詳細資訊，請參閱[階層式更新](../data-tools/hierarchical-update.md)和 [TableAdapterManager 概觀](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)。  
  
 當您執行專案時，控制項會顯示資料來源中的第一筆記錄。  您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。  
  
#### 捲動資料列  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 如需如何將更新傳送至具類型資料集和資料庫的相關資訊，請參閱[如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [使用在 Office 方案概觀中的本機資料庫檔案](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [連接至 Windows Form 應用程式中的資料](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  