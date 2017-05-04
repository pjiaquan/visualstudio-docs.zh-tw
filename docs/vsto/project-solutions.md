---
title: "專案方案 | Microsoft Docs"
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
  - "專案 [Visual Studio 中的 Office 程式開發]，Project"
  - "Office 方案 [Visual Studio 中的 Office 程式開發]，Project"
  - "專案 [Visual Studio 中的 Office 程式開發]"
  - "範本 [Visual Studio 中的 Office 程式開發]，Project"
  - "Office 專案 [Visual Studio 中的 Office 程式開發]，Project"
  - "方案 [Visual Studio 中的 Office 程式開發]，Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# 專案方案
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 提供的專案範本可用來建立 Microsoft Office Project 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Project、擴充 Project 功能，或自訂 Project 的使用者介面 \(UI\)。  
  
 如需 VSTO 增益集的詳細資訊，請參閱下列主題：[VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)和 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。 如果您是使用 Microsoft Office 程式設計的新手，請參閱[使用者入門 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## 使用 Project 物件模型自動化 Project  
 Project 物件模型公開許多可用於自動化 Project 的類別。 這些類別可讓您撰寫程式碼以完成一般工作，例如以程式設計方式建立和修改專案中的工作。  
  
 若要存取 VSTO 增益集中的 Project 物件模型，請使用專案中 `ThisAddIn` 類別的 `Application` 欄位。`Application` 欄位傳回的 Microsoft.Office.Interop.MsProject.Application  物件，代表專案目前的執行個體。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
 呼叫 Project 物件模型時，您使用的類型是由 Project 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與專案中 COM 物件模型之間的橋樑。 Project 主要 Interop 組件中的所有類型都定義在 Microsoft.Office.Interop.MSProject 命名空間中。 如需主要 Interop 組件的詳細資訊，請參閱 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)和 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## 使用 Project 物件模型文件  
 如需 Project 物件模型的完整資訊，您可以參考 Project VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications \(VBA\) 程式碼時的專案物件模型。 如需詳細資訊，請參閱 [Project 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199771)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 Project 主要 Interop 組件 \(PIA\) 中的類型和成員。 例如，VBA 物件模型參考中的 Calendar 物件會對應至 Project PIA 中的 Microsoft.Office.Interop.MSProject.Calendar 類型。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Project VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C\# 程式碼。  
  
> [!NOTE]  
>  目前沒有 Project 主要 Interop 組件的參考文件。  
  
### Project 主要 Interop 組件中的基礎結構類型  
 在您撰寫使用 Project PIA 的程式碼時，可能會注意到未在 VBA 參考中描述的許多類型。 這些額外類型會協助將 Project 的 COM 架構物件模型轉譯成 Managed 程式碼，不適合直接在程式碼中使用。  
  
 如需詳細資訊，請參閱 [Office 主要 Interop 組件中的類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=189592)。  
  
## 自訂 Project 的使用者介面  
 您可以使用下列方式自訂 Project UI。  
  
|工作|如需詳細資訊|  
|--------|------------|  
|在 Project 的功能區中加入自訂索引標籤。|[功能區概觀](../vsto/ribbon-overview.md)|  
  
 如需自訂 Project 與其他 Microsoft Office 應用程式 UI 的詳細資訊，請參閱 [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## 請參閱  
 [逐步解說：建立 Project 的第一個 VSTO 增益集](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [Office 程式開發中的 Project 2010 和 Project Server 2010](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  