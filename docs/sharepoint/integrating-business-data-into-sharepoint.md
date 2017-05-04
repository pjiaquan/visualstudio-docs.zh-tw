---
title: "將商業資料整合至 SharePoint | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio 中的 SharePoint 開發], 彙總資料"
  - "BDC [Visual Studio 中的 SharePoint 開發], 商務資料"
  - "BDC [Visual Studio 中的 SharePoint 開發], 建立模型"
  - "BDC [Visual Studio 中的 SharePoint 開發], 資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 彙總資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 商務資料"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 建立模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 資料"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 將商業資料整合至 SharePoint
  您可以將商務資料整合至 SharePoint。  商務資料可能來自於後端伺服器應用程式，例如 [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)]、Siebel 和 SAP，或者是 Web 服務。  使用者可以在 SharePoint 中使用外部清單或商務資料 Web 組件來檢視、加入、更新或刪除商務資料。使用者也可以在 Microsoft Office 應用程式 \(例如 Microsoft Outlook\) 中離線存取這些資料。  如需詳細資訊，請參閱 [如何顯示外部資料](http://go.microsoft.com/fwlink/?LinkId=169295)。  
  
 若要將資料整合至 SharePoint，請建立商務資料連接 \(BDC\) 服務的模型。  BDC 服務是 SharePoint 中的應用程式，可儲存商業應用程式中資料的相關資訊。  如需詳細資訊，請參閱 [商務資料連接 \(BDC\) 服務](http://go.microsoft.com/fwlink/?LinkID=169276)。  
  
## Visual Studio 中的模型  
 Visual Studio 中的模型可讓您撰寫自訂程式碼來擷取和更新後端資料來源的資料。  您也可以彙總多個資料來源的資料。  例如，您可以顯示客戶清單，其中包含來自於 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] 資料庫和 Web 服務的資料。  
  
 您也可以匯入已部署至 SharePoint 的模型。  匯入模型之後，您可以加入自訂程式碼，或直接使用 Visual Studio 封裝並部署模型至多個 SharePoint 伺服器陣列。  如需詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
## 在 Visual Studio 中設計模型  
 您可以使用設計工具和多個工具視窗來設計模型。  當您設計模型時，Visual Studio 會產生模型 XML。  如需詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
 模型包含實體和方法。  
  
### 實體  
 實體會描述欄位集合。  例如，實體可表示資料庫中的資料表。  實體在 SharePoint 中會呈現為外部內容類型。  如需外部內容類型的詳細資訊，請參閱 [什麼是外部內容類型?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### 方法  
 方法可以讓外部內容類型的消費者在實體的欄位上執行動作。  例如，Updater 方法可讓使用者變更客戶的地址和出生日期，其中 `Address` 和 `BirthDate` 便是 `Customer` 實體的欄位。  
  
 Visual Studio 會針對模型中的每個實體產生服務程式碼檔。  當您將方法加入至模型時，Visual Studio 會在服務程式碼檔中產生對應的方法。  請將程式碼加入每個方法來執行適當工作。  例如，如果您將 Creator 方法加入至模型，Visual Studio 會在服務程式碼檔中產生 Creator 方法。  當使用者在以模型為基礎的清單中按一下 \[**新增項目**\] 按鈕時，BDC 服務會呼叫此方法。  因此，請在 Creator 方法中加入可將新資料加入至資料來源的程式碼。  如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)|顯示如何建立新模型，或匯入從 SharePoint 匯出的模型。|  
|[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)|說明如何使用 Visual Studio 設計工具設計模型的項目。|  
|[在建置方案使用 BCS 時，何時使用 SharePoint Designer 與 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=183448)|幫助您決定是要使用 Visual Studio 還是 SharePoint Designer 來建立 BDC 的模型。|  
  
  