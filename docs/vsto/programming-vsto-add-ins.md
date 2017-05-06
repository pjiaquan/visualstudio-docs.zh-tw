---
title: "VSTO 增益集程式設計"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Addin"
  - "VST.ProjectItem.AddinProject"
  - "thisAddIn"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ICustomTaskPaneConsumer 介面"
  - "增益集 [Visual Studio 中的 Office 程式開發]，程式設計"
  - "IRibbonExtensibility 介面"
  - "UI 自訂 [Visual Studio 中的 Office 程式開發]"
  - "Office 應用程式 [Visual Studio 中的 Office 程式開發]，應用程式層級增益集"
  - "程式設計 [Visual Studio 中的 Office 程式開發]，應用程式層級增益集"
  - "ThisAddIn 類別"
  - "使用者介面 [Visual Studio 中的 Office 程式開發]，自訂"
  - "撰寫 Office 方案的程式碼"
  - "主項目 [Visual Studio 中的 Office 程式開發]，增益集"
  - "應用程式開發 [Visual Studio 中的 Office 程式開發]，應用程式層級增益集"
  - "增益集 [Visual Studio 中的 Office 程式開發]，ThisAddIn 類別"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]，ThisAddIn 類別"
  - "FormRegionStartup 介面"
  - "ThisAddIn_Startup"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]，程式設計"
  - "ThisAddIn_Shutdown"
ms.assetid: c534786d-2833-4afa-9e4c-4633f46b9eed
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# VSTO 增益集程式設計
  當您建立 VSTO 增益集來擴充 Microsoft Office 應用程式時，會直接針對專案中的 `ThisAddIn` 類別撰寫程式碼。 您可以使用這個類別來執行工作，例如存取 Microsoft Office 主應用程式的物件模型、自訂應用程式的使用者介面 \(UI\)，以及將 VSTO 增益集中的物件公開給其他 Office 解決方案。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 撰寫 VSTO 增益集專案中的程式碼，在某些方面不同於撰寫 Visual Studio 中其他類型專案的程式碼。 其中有許多差異的原因來自於將 Office 物件模型公開給 Managed 程式碼的方式。 如需詳細資訊，請參閱[撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)。  
  
 如需可用 Visual Studio 中的 Office 程式開發工具建立之 VSTO 增益集和其他類型方案的一般資訊，請參閱 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
## 使用 ThisAddIn 類別  
 您可以在 `ThisAddIn` 類別中開始撰寫 VSTO 增益集程式碼。 Visual Studio 會在 VSTO 增益集專案的 ThisAddIn.vb \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) 或 ThisAddIn.cs \(C\#\) 程式碼檔中，自動產生這個類別。 當 Microsoft Office 應用程式載入您的 VSTO 增益集時，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會自動為您具現化這個類別。  
  
 `ThisAddIn` 類別有兩個預設事件處理常式。 若要在載入 VSTO 增益集時執行程式碼，請將程式碼加入`ThisAddIn_Startup` 事件處理常式中。 若要在卸載 VSTO 增益集之前執行程式碼，請將程式碼加入 `ThisAddIn_Shutdown` 事件處理常式。 如需這些事件處理常式的詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
> [!NOTE]  
>  在 Outlook 中，當卸載 VSTO 增益集時，預設不一定會呼叫 `ThisAddIn_Shutdown` 事件處理常式。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
### 存取主應用程式的物件模型  
 若要存取主應用程式的物件模型，請使用 `ThisAddIn` 類別的 `Application` 欄位。 這個欄位會傳回代表主應用程式之目前執行個體的物件。 下表列出每個 VSTO 增益集專案中 `Application` 欄位的傳回值類型。  
  
|主應用程式|傳回值類型|  
|-----------|-----------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 下列程式碼範例示範如何使用 `Application` 欄位，在 Microsoft Office Excel 的 VSTO 增益集中建立新的活頁簿。 這個範例適合從 `ThisAddIn` 類別執行。  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 若要從 `ThisAddIn` 類別外執行相同的動作，請使用 `Globals` 物件存取 `ThisAddIn` 類別。 如需 `Globals` 物件的詳細資訊，請參閱 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 如需特定的 Microsoft Office 應用程式之物件模型的詳細資訊，請參閱下列主題：  
  
-   [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)  
  
-   [Word 物件模型概觀](../vsto/word-object-model-overview.md)  
  
-   [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath 方案](../vsto/infopath-solutions.md)  
  
-   [PowerPoint 方案](../vsto/powerpoint-solutions.md)  
  
-   [專案方案](../vsto/project-solutions.md)  
  
-   [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> 啟動 Office 應用程式時存取文件  
 當您啟動 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 應用程式時，並非所有應用程式都會自動開啟文件；而當您啟動 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 應用程式時，所有應用程式都不會開啟文件。 因此，如果程式碼需要開啟文件，請勿將程式碼加入 `ThisAdd-In_Startup` 事件處理常式。 相反地，請將程式碼加入 Office 應用程式在使用者建立或開啟文件時所引發的事件。 如此可確保程式碼對文件執行作業之前，該文件已處於開啟狀態。  
  
 下列程式碼範例只有在使用者建立文件或開啟現有文件時，才適用於 Word 文件。  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#3)]  
  
### 用於其他工作的 ThisAddIn 成員  
 下表說明其他常見工作，並顯示可以用來執行這些工作的 `ThisAddIn` 類別。  
  
|工作|要使用的成員|  
|--------|------------|  
|載入 VSTO 增益集時，執行程式碼以初始化 VSTO 增益集。|將程式碼加入 `ThisAddIn_Startup` 方法。 這是 <xref:Microsoft.Office.Tools.AddInBase.Startup> 事件的預設事件處理常式。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。|  
|卸載 VSTO 增益集之前，執行程式碼以清除 VSTO 增益集所使用的資源。|將程式碼加入 `ThisAddIn_Shutdown` 方法。 這是 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 事件的預設事件處理常式。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。 **Note:**  在 Outlook 中，當卸載 VSTO 增益集時，預設不一定會呼叫 `ThisAddIn_Startup` 事件處理常式。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。|  
|顯示自訂工作窗格。|使用 `CustomTaskPanes` 欄位。 如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)。|  
|將 VSTO 增益集中的物件公開給其他 Microsoft Office 方案。|覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 方法。 如需詳細資訊，請參閱[從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)。|  
|實作擴充性介面來自訂 Microsoft Office system 中的功能。|覆寫 <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> 方法以傳回實作介面的類別執行個體。 如需詳細資訊，請參閱[使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)。 **Note:**  若要自訂功能區 UI，您也可以覆寫 <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> 方法。|  
  
### 了解 ThisAddIn 類別的設計  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 為目標的專案中，<xref:Microsoft.Office.Tools.AddIn> 是一種介面。`ThisAddIn` 類別衍生自 <xref:Microsoft.Office.Tools.AddInBase> 類別。 這個基底類別會將其成員的所有呼叫重新導向至 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中 <xref:Microsoft.Office.Tools.AddIn> 介面的內部實作。  
  
 在 Outlook VSTO 增益集專案中，`ThisAddIn` 類別是衍生自以 .NET Framework 3.5 為目標之專案中的 Microsoft.Office.Tools.Outlook.OutlookAddIn 類別，以及以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 為目標之專案中的 <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase>。 這些基底類別提供了一些額外的功能來支援表單區域。 如需表單區域的詳細資訊，請參閱 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
## 自訂 Microsoft Office 應用程式的使用者介面  
 您可以使用 VSTO 增益集，以程式設計方式自訂 Microsoft Office 應用程式的 UI。 例如，您可以自訂功能區、顯示自訂工作窗格，或建立 Outlook 的自訂表單區域。 如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
 Visual Studio 提供可用來建立自訂工作窗格、功能區自訂和 Outlook 表單區域的設計工具和類別。 這些設計工具和類別有助於簡化自訂這些功能的程序。 如需詳細資訊，請參閱[自訂工作窗格](../vsto/custom-task-panes.md)、[功能區設計工具](../vsto/ribbon-designer.md)和[建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)。  
  
 如果您想要使用類別和設計工具不支援的方式，來自訂上述其中一項功能，您也可以透過在 VSTO 增益集中實作*「擴充性介面」*\(Extensibility Interface\)，來自訂這些功能。 如需詳細資訊，請參閱[使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)。  
  
 此外，您也可以藉由產生可擴充文件和活頁簿行為的主項目，來修改 Word 文件和 Excel 活頁簿的 UI。 這可讓您將 Managed 控制項加入文件和工作表。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## 從其他方案呼叫 VSTO 增益集的程式碼  
 您可以將 VSTO 增益集中的物件公開給其他方案 \(包括其他 Office 方案\)。 如果您想要讓其他方案也能使用 VSTO 增益集提供的服務，這就很有用。 例如，如果您的 Microsoft Office Excel VSTO 增益集會計算 Web 服務的財務資料，則其他方案可以在執行階段呼叫這個 Excel VSTO 增益集來執行這些計算。  
  
 如需詳細資訊，請參閱[從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)。  
  
## 請參閱  
 [開發 Office 方案](../vsto/developing-office-solutions.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [從其他 Office 方案呼叫 VSTO 增益集的程式碼](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [逐步解說：從 VBA 呼叫 VSTO 增益集的程式碼](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [使用擴充性介面自訂 UI 功能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  