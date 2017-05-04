---
title: "如何：將物件的資料填入文件 | Microsoft Docs"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，填入資料"
  - "資料 [Visual Studio 中的 Office 程式開發]，加入文件"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 如何：將物件的資料填入文件
  在 Microsoft Office Word 文件層級專案中使用資料物件存取資料時，其運作方式與在 Windows Form 專案中的運作方式相同。 您可以使用相同的工具和程式碼，將資料從物件帶入方案中，也可以使用 Windows Form 控制項顯示資料。 此外，也可以使用主控制項來顯示資料。 主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。 如需詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 您必須先完成三個基本步驟，才能將物件的資料填入文件：  
  
-   將控制項加入可繫結到資料的文件。  
  
-   將資料物件加入文件。  
  
-   將資料物件連接至 BindingSource。  
  
## 加入資料物件  
  
#### 若要加入資料物件  
  
-   開啟 \[資料來源\] 視窗，並從物件建立資料來源。 如需詳細資訊，請參閱[如何：連接至物件中的資料](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b)。  
  
## 將資料物件連接至 BindingSource  
 在文件層級專案中，您可以在設計階段將控制項加入文件，並將控制項繫結至資料。  
  
 在 VSTO 增益集專案中，您可以在執行階段建立並繫結控制項。  
  
### 文件層級專案  
  
##### 若要將資料物件連接至 BindingSource  
  
1.  將想要的資料欄位從 \[資料來源\] 視窗拖曳至您的文件。 這樣會自動建立控制項。  
  
2.  在程式碼中，針對您為資料來源所選取的物件類型，建立執行個體。  
  
3.  將該執行個體指派給 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性。  
  
### 應用程式層級專案  
  
##### 若要將資料物件連接至 BindingSource  
  
1.  在程式碼中，針對與資料來源相關聯的物件類型，建立執行個體。  
  
2.  建立 <xref:System.Windows.Forms.BindingSource> 的執行個體。  
  
3.  將該資料來源執行個體指派給 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性。  
  
4.  將資料來源做為資料繫結加入控制項中。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [資料來源概觀](../data-tools/add-new-data-sources.md)   
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：從主控制項中使用資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [連接至 Windows Form 應用程式中的資料](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  