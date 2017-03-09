---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 提供多種工具供您使用 Windows Communication Foundation \(WCF\) 和 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，這些是用於建立分散式應用程式的 Microsoft 技術。  本主題提供以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 為主的服務簡介。  
  
## 何謂 WCF？  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 是一種統一架構，用於建立安全、可靠、可交易且具互通性的分散式應用程式。  在舊版 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，有一些可用於在應用程式之間進行通訊的技術。  
  
 如果您要藉由在任何平台都能存取資料的方式來共用資訊，可能就要使用 Web 服務 \(也就是 ASMX Web 服務\)。  如果您只是要在用戶端和執行 Windows 作業系統的伺服器之間移動資料，可以使用 .NET 遠端處理。  如果要進行交易式通訊，可以使用企業服務 \(DCOM\)；而如果要用佇列模型，則可以使用訊息佇列 \(也稱為 MSMQ\)。  
  
 WCF 會在統一的程式撰寫模型 \(Programming Model\) 下，將這些技術統籌為一種功能。  這樣可簡化開發分散式應用程式的工作。  
  
#### 何謂 WCF 資料服務  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 是與資料庫直接互動的服務，可讓您使用標準 HTTP 動作 \(例如 GET、POST、PUT 或 DELETE\) 傳回資料。  一般而言，[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 是用於建立、更新或刪除資料庫記錄之應用程式的好選擇。  如需詳細資訊，請參閱 [ADO.NET Data Services 架構](http://go.microsoft.com/fwlink/?LinkID=119952)。  
  
### WCF 程式撰寫模型  
 WCF 程式撰寫模型主要是以兩個實體 \(WCF 服務和 WCF 用戶端\) 之間的通訊為基礎。  程式撰寫模型會封裝在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的 <xref:System.ServiceModel> 命名空間中。  
  
#### WCF 服務  
 WCF 服務則是以介面為基礎，這個介面會定義服務和用戶端之間的合約。  這個服務會使用 <xref:System.ServiceModel.ServiceContractAttribute> 屬性加上標記，如下列程式碼所示：  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 您可以使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性為 WCF 服務所公開的函式或方法加上標記，就可以定義它們。  此外，也可以使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性為複合型別加上標記，即可公開序列化的資料。  這樣可在用戶端中啟用資料繫結。  
  
 介面與其方法完成定義之後，就會封裝在實作介面的類別中。  單一 WCF 服務類別可以實作多個服務合約。  
  
 透過所謂的「*端點*」\(Endpoint\) 公開 WCF 服務，便能使用該服務。  端點可提供唯一一種與服務通訊的方式。您無法如同使用其他類別一樣，透過直接參考來存取服務。  
  
 端點是由位址、繫結和合約所組成。  位址會定義服務的位置，可以是 URL、FTP 位址，或是網路或本機路徑。  繫結則會定義您與服務通訊的方式。  WCF 繫結可提供多樣化的模型，讓您指定 HTTP 或 FTP 等通訊協定、並指定 Windows 驗證或使用者名稱和密碼這類安全性機制等等。  合約則包含 WCF 服務類別所公開的作業。  
  
 您可以針對單一 WCF 服務公開多個端點。  這樣可讓不同的用戶端以不同的方式與相同的服務通訊。  例如，銀行服務可為多位員工提供一個端點，並為多個外部客戶提供另一個端點，而這些端點都使用不同的位址、繫結及\/或合約。  
  
#### WCF 用戶端  
 WCF 用戶端是由 *Proxy* 和端點組成，Proxy 可讓應用程式與 WCF 服務通訊，而此端點符合針對服務所定義的端點。  Proxy 是在用戶端的 app.config 檔案中產生，其中包含服務所公開之型別和方法的相關資訊。  針對公開多個端點的服務，用戶端可以選取一個最符合需求的端點。例如，要透過 HTTP 進行通訊並使用 Windows 驗證。  
  
 建立 WCF 用戶端之後，再於程式碼中參考服務，就如同參考其他物件一樣。  例如，若要呼叫稍早提及的 `GetData` 方法，您可以撰寫類似如下的程式碼：  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Visual Studio 中的 WCF 工具  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 提供多種工具，可協助您建立 WCF 服務和 WCF 用戶端。  如需示範這些工具的逐步解說，請參閱[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。  
  
### 建立及測試 WCF 服務  
 您可以使用 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本為基礎，快速建立自己的服務。  接著，再使用 WCF 服務自動裝載和 WCF 測試用戶端，對服務進行偵錯和測試。  這些工具可提供快速且便利的偵錯與測試循環，並去除在早期認可裝載模型的需求。  
  
#### WCF 範本  
 WCF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本可提供服務部署的基本類別結構。  您可以在 \[**加入新的專案**\] 對話方塊中找到一些可用的 WCF 範本。  這些範本包括 WCF 服務庫專案、WCF 服務網站和 WCF 服務項目等範本。  
  
 當您選取範本時，會針對服務合約、服務實作和服務組態加入檔案。  所有必要屬性則都已加入，如此您便能建立簡單的 "Hello World" 服務型別，而完全不需要撰寫程式碼。  您當然想要加入程式碼以針對實際服務提供函式和方法，不過範本可以先為您提供基本基礎。  
  
 若要進一步了解 WCF 範本，請參閱 [WCF Visual Studio 範本](../Topic/WCF%20Visual%20Studio%20Templates.md)。  
  
#### WCF 服務裝載  
 當您啟動 WCF 服務專案的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具 \(按 F5 即可\) 時，WCF 服務主機就會自動開始在本機裝載服務。  WCF 服務主機會列舉 WCF 服務專案中的服務、載入專案組態，並具現化找到之每個服務的主機。  
  
 使用 WCF 服務主機時，您可以在開發期間測試 WCF 服務，而不需要撰寫額外的程式碼或認可特定主機。  
  
 若要進一步了解 WCF 服務主機，請參閱 [WCF 服務主機 \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md)。  
  
#### WCF 測試用戶端  
 WCF 測試用戶端工具可讓您輸入測試參數、將該輸入內容提交至 WCF 服務，然後檢視服務傳回的回應。  當您結合 WCF 測試用戶端和 WCF 服務主機時，就可以更方便地測試服務。  
  
 按 F5 開始偵錯 WCF 服務專案時，\[WCF 測試用戶端\] 隨即開啟，並顯示組態檔中定義的服務端點清單。  您可以測試參數並啟動服務，再重複此程序以連續測試及驗證服務。  
  
 若要進一步了解 WCF 測試用戶端，請參閱 [WCF 測試用戶端 \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md)。  
  
### 在 Visual Studio 中存取 WCF 服務  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]簡化了建立 WCF 用戶端，會自動產生 proxy，並利用新增的服務端點的工作**加入服務參考**對話方塊。  所有需要的組態資訊都已加入至 app.config 檔案。絕大多數您只需要具現化服務就能使用。  
  
 \[**加入服務參考**\] 對話方塊可讓您輸入服務的位址，或者搜尋已在方案中定義的服務。  這個對話方塊會傳回服務清單，以及這些服務所提供的作業。  它也能讓您根據將在程式碼中參考的服務來定義命名空間。  
  
 \[**設定服務參考**\] 對話方塊可讓您自訂服務的組態。  您可以變更服務的位址、指定存取層級、非同步行為和訊息合約型別，並可設定型別重複使用。  
  
## How to： 選取服務端點  
 某些 Windows Communication Foundation \(WCF\) 服務會公開多個端點，使用戶端能夠透過這些端點與服務進行通訊。  例如，服務可能會公開一個使用 HTTP 繫結和使用者名稱\/密碼安全性的端點，以及另一個使用 FTP 和 Windows 驗證的端點。  第一個端點可能會由防火牆外部存取服務的應用程式使用，而第二個端點可能是在內部網路使用。  
  
 在這種情況下，您可以將 `endpointConfigurationName` 當做參數，指定給服務參考的建構函式 \(Constructor\)。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要選取服務端點  
  
1.  加入 WCF 服務的參考。  如需詳細資訊，請參閱 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)。  
  
2.  在 \[程式碼編輯器\] 中，加入服務參考的建構函式：  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  以服務參考的命名空間取代 *ServiceReference*，並以服務的名稱取代 *Service1Client*。  
  
3.  此時將會顯示 IntelliSense 清單，其中包含建構函式的多載。  選取 `endpointConfigurationName As String` 多載。  
  
4.  在多載之後輸入 `=` *ConfigurationName*，其中 *ConfigurationName* 是您要使用的端點名稱。  
  
    > [!NOTE]
    >  如果您不知道可用的端點名稱，可以在 app.config 檔案內找到它們。  
  
#### 若要找出 WCF 服務的可用端點  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下包含服務參考之專案的 app.config 檔案，然後按一下 \[**開啟**\]。  檔案將會顯示在 \[程式碼編輯器\] 中。  
  
2.  在檔案中搜尋 `<Client>` 標記 \(Tag\)。  
  
3.  在 `<Client>` 標記下方搜尋以 `<Endpoint>` 為開頭的標記。  
  
     如果服務參考提供了多個端點，則會出現兩個或多個 `<Endpoint` 標記。  
  
4.  在 `<EndPoint>` 標記內部，您將會找到 `name="`*SomeService*`"` 參數 \(其中 *SomeService* 代表端點名稱\)。  這個端點名稱可以傳遞給服務參考之建構函式的 `endpointConfigurationName As String` 多載。  
  
## How to： 以非同步方式呼叫服務方法  
 Windows Communication Foundation \(WCF\) 服務中的大部分方法都可以進行同步呼叫或非同步呼叫。  非同步呼叫方法時，可讓慢速連接的應用程式在呼叫方法時繼續運作。  
  
 根據預設，將服務參考加入至專案時，會設定為同步呼叫方法。  藉由變更 \[**設定服務參考**\] 對話方塊中的設定，您可以將此行為變更為非同步呼叫方法。  
  
> [!NOTE]
>  這個選項是針對服務設定的。  如果非同步呼叫服務的一個方法，則必須非同步呼叫所有方法。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 若要非同步呼叫服務方法  
  
1.  在 \[**方案總管**\] 中選取服務參考。  
  
2.  按一下 \[**專案**\] 功能表上的 \[**設定服務參考**\]。  
  
3.  在 \[**設定服務參考**\] 對話方塊中，選取 \[**產生非同步作業**\] 核取方塊。  
  
## How to： 將服務所傳回的資料繫結  
 您可以將 Windows Communication Foundation \(WCF\) 服務傳回的資料繫結至控制項，就如同將任何其他資料來源繫結至控制項一樣。  當您加入 WCF 服務的參考時，如果服務包含會傳回資料的複合型別，則會將這些複合型別自動加入至 \[**資料來源**\] 視窗。  
  
#### 若要將控制項繫結至 WCF 服務傳回的單一資料欄位  
  
1.  按一下 \[**資料**\] 功能表上的 \[**顯示資料來源**\]。  \[**資料來源**\] 視窗隨即出現。  
  
2.  在 \[**資料來源**\] 視窗中，展開服務參考的節點。  服務所傳回的所有複合型別隨即出現。  
  
3.  展開型別的節點。  該型別的資料欄位隨即出現。  
  
4.  選取欄位並按一下下拉箭號，顯示資料型別的適用控制項清單。  
  
5.  按一下您要繫結的控制項型別。  
  
6.  將欄位拖曳至表單上。  控制項就會與 <xref:System.Windows.Forms.BindingSource> 元件和 <xref:System.Windows.Forms.BindingNavigator> 元件一併新增至表單。  
  
7.  重複執行步驟 4 到 6，設定要繫結的任何其他欄位。  
  
#### 若要將控制項繫結至 WCF 服務傳回的複合型別  
  
1.  選取 \[**資料**\] 功能表上的 \[**顯示資料來源**\]，  \[**資料來源**\] 視窗隨即出現。  
  
2.  在 \[**資料來源**\] 視窗中，展開服務參考的節點。  服務所傳回的所有複合型別隨即出現。  
  
3.  選取型別節點並按一下下拉箭號，顯示可用的選項清單。  
  
4.  按一下 \[**DataGridView**\] 顯示方格中的資料，或按一下 \[**詳細資料**\] 顯示個別控制項中的資料。  
  
5.  將節點拖曳至表單上。  這些控制項就會與 <xref:System.Windows.Forms.BindingSource> 元件和 <xref:System.Windows.Forms.BindingNavigator> 元件一併新增至表單。  
  
## How to： 設定服務以重複使用現有的型別  
 當服務參考加入至專案時，本機專案中會產生服務中定義的所有型別。  在許多情況下，當服務使用一般 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 型別，或當型別是在共用程式庫中定義時，這便會造成重複型別。  
  
 為了避免這個問題，參考組件中的型別預設為共用。  如果您要停用一個或多個組件的型別共用，可以在 \[**設定服務參考**\] 對話方塊中進行這項作業。  
  
#### 若要停用單一組件中的型別共用  
  
1.  在 \[**方案總管**\] 中選取服務參考。  
  
2.  按一下 \[**專案**\] 功能表上的 \[**設定服務參考**\]。  
  
3.  在 \[**設定服務參考**\] 對話方塊中，選取 \[**重複使用指定的參考組件中的型別**\]。  
  
4.  針對您要啟用型別共用的每個組件，選取其核取方塊。  若要停用組件的型別共用，請清除核取方塊。  
  
#### 若要停用所有組件中的型別共用  
  
1.  在 \[**方案總管**\] 中選取服務參考。  
  
2.  按一下 \[**專案**\] 功能表上的 \[**設定服務參考**\]。  
  
3.  在 \[**設定服務參考**\] 對話方塊中，清除 \[**重複使用參考組件中的型別**\] 核取方塊。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|提供逐步示範，說明如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立和使用 WCF 服務。|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|提供逐步示範，說明如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立和使用 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。|  
|[使用 WCF 開發工具](../Topic/Using%20the%20WCF%20Development%20Tools.md)|討論如何建立和測試 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 WCF 服務。|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|說明如何在專案中加入、更新或移除 WCF 服務。|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|討論如何參考和使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]。|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|說明如何將 XML \(ASMX\) Web 服務的參考加入至專案。|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|說明使用服務參考時的常見錯誤，以及如何避免這些錯誤。|  
|[偵錯 WCF 服務](../debugger/debugging-wcf-services.md)|描述在偵錯 WCF 服務時可能會遇到的常見偵錯問題和技術。|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|說明如何使用 WCF 提供網站的角色服務。|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/zh-tw/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|說明 .NET Compact Framework 中的 WCF 訊息層支援。|  
|[逐步解說：建立 N\-Tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|提供逐步指示，說明如何建立具型別資料集，並將 TableAdapter 和資料集程式碼分隔成多個專案。|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|描述 \[**加入服務參考**\] 對話方塊的使用者介面項目。|  
|[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)|描述 \[**設定服務參考**\] 對話方塊的使用者介面項目。|  
  
## 參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>