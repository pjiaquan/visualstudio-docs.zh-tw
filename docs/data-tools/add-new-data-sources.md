---
title: "資料來源概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "資料 [Visual Studio], 資料來源"
  - "資料來源"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料來源概觀
「資料來源」\(Data Source\) 表示應用程式可使用的資料。  更確切地說，資料來源就是要在應用程式中使用的資料。  資料來源可以從資料庫 \(包括本機資料庫檔案\)、服務和物件中取得。  
  
 加入專案中的資料來源會顯示在 \[**資料來源**\] 視窗。  在許多情況下，您可以將資料來源拖曳到 Windows Form、WPF 和 Silverlight Designer，以建立繫結至基礎資料的控制項。  如需詳細資訊，請參閱[將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 Visual Studio 提供許多工具，可用來建立和編輯應用程式中的資料來源。  在 Visual Studio 專案中，會以實體資料模型、資料集、服務傳回的 Proxy 物件或其他物件類型表示資料來源，視基礎資料存放區傳回的物件而定。  
  
 您可以使用 \[**資料來源組態精靈**\] 建立及編輯資料來源。  
  
## 從資料庫建立資料來源  
 您可以從資料庫建立資料來源，其方式是執行 \[**資料來源組態精靈**\]，並選取 \[**資料庫**\] 資料來源類型。  如需詳細資訊，請參閱[如何：連接至資料庫中的資料](../data-tools/how-to-connect-to-data-in-a-database.md)。  
  
 當您從資料庫建立資料來源時，Visual Studio 會產生「*資料模型*」\(Data Model\) 並將它加入至專案。  資料模型是資料庫基礎資料的強類型、可程式檢視。  您可以使用 Visual Studio 建立下列類型的資料模型：  
  
-   以[實體資料模型](../Topic/Entity%20Data%20Model.md)為基礎的概念模型。  這種模型可用於 Entity Framework 或 WCF 資料服務。  如需詳細資訊，請參閱[Entity Framework 概觀](../Topic/Entity%20Framework%20Overview.md)與[WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md)。  
  
-   具類型的資料集。  如需詳細資訊，請參閱[使用 Visual Studio 中的資料集](../data-tools/dataset-tools-in-visual-studio.md)。  
  
-   LINQ to SQL 類別。  如需詳細資訊，請參閱[LINQ to SQL](../Topic/LINQ%20to%20SQL.md)。  
  
    > [!NOTE]
    >  不同於以實體資料模型為基礎的概念模型和資料集，LINQ to SQL 類別無法透過 \[**資料來源組態精靈**\] 來建立。  它們也不會出現在 \[**資料來源**\] 視窗中，因此無法拖曳至設計工具建立資料繫結控制項。  不過，您可以根據 LINQ to SQL 類別建立物件資料來源，並將這些物件拖曳至設計工具。  如需詳細資訊，請參閱[HOW TO：建立對應到資料表和檢視的 LINQ to SQL 類別 \(O\/R 設計工具\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)。  
  
### 從區域資料庫檔案建立的資料來源  
 您也可以從下列類型的資料庫檔案建立資料來源：Access 資料庫 \(.mdb 檔案\)、SQL Server Express LocalDB 資料庫 \(.mdf 檔案\) 和 SQL Server Express 資料庫 \(.mdf 檔案\)。  從這些資料庫檔案建立資料來源時，可以將資料庫檔案直接加入至專案。  如需詳細資訊，請參閱下列主題：  
  
-   [區域資料概觀](../data-tools/local-data-overview.md)  
  
-   [如何：管理專案中的本機資料檔](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## 從服務建立的資料來源  
 您可以從服務建立資料來源，其方式是執行 \[**資料來源組態精靈**\]，並選取 \[**服務**\] 資料來源類型。  如需詳細資訊，請參閱[如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
 當您從服務建立資料來源時，Visual Studio 會在專案中加入服務參考。  Visual Studio 也會建立對應於服務所傳回之物件的 Proxy 物件。  例如，傳回資料集的服務會在專案中表示為資料集，而傳回特定類型的服務，則會在專案中表示為傳回的類型。  
  
 您可以從下列服務類型建立資料來源：  
  
-   WCF 資料服務。  如需詳細資訊，請參閱[概觀](../Topic/WCF%20Data%20Services%20Overview.md)。  
  
-   Windows Communication Foundation \(WCF\) 服務。  如需詳細資訊，請參閱[Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)。  
  
-   Web 服務。  如需詳細資訊，請參閱[Not in Build: Introduction to Programming Web Services in Managed Code](http://msdn.microsoft.com/zh-tw/bd8861f3-39e1-4c06-995e-677e007eb961)。  
  
    > [!NOTE]
    >  \[**資料來源**\] 視窗中出現的項目需視服務所傳回的資料而定。  某些服務可能不會提供足夠的資訊，讓 \[**資料來源組態精靈**\] 建立可繫結的物件。  例如，如果服務傳回不具類型的資料集，則完成精靈之後，在 \[**資料來源**\] 視窗中不會出現任何項目。  這是因為不具類型的資料集不會提供結構描述，所以精靈沒有充分資訊來建立資料來源。  
  
## 從物件建立資料來源  
 您可以從公開一個或多個公用屬性的任何物件建立資料來源，其方式是執行 \[**資料來源組態精靈**\]，然後選取 \[**物件**\] 資料來源類型。  物件的所有公用屬性都會顯示在 \[**資料來源**\] 視窗中。  如需詳細資訊，請參閱[如何：連接至物件中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
 如需繫結至物件的詳細資訊，請參閱 [Visual Studio 中的物件繫結](../data-tools/bind-objects-in-visual-studio.md)。  
  
## 從 SharePoint 清單建立的資料來源  
 您可以從 SharePoint 清單建立資料來源，其方式是執行 \[**資料來源組態精靈**\]，並選取 \[**SharePoint**\] 資料來源類型。  SharePoint 透過 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 公開資料，因此建立 SharePoint 資料來源和從服務建立資料來源效果相同。  在 \[**資料來源組態精靈**\] 中選取 \[**SharePoint**\] 項目，會開啟 \[**加入服務參考**\] 對話方塊，您可以在此指向 SharePoint 伺服器連接至 SharePoint 資料來源。  如需詳細資訊，請參閱[如何：連接至服務中的資料](../data-tools/how-to-connect-to-data-in-a-service.md)。  
  
## 請參閱  
 [將 Windows Form 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)   
 [資料來源視窗](../Topic/Data%20Sources%20Window.md)   
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式以接收資料](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)   
 [驗證資料](../Topic/Validating%20Data.md)   
 [儲存資料](../data-tools/saving-data.md)