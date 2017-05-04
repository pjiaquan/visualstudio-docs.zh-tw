---
title: "設計商務資料連接模型 | Microsoft Docs"
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
  - "BDC [Visual Studio 中的 SharePoint 開發], 設計模型"
  - "商務資料連接服務 [Visual Studio 中的 SharePoint 開發], 設計模型"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# 設計商務資料連接模型
  您可以將實體和方法加入至模型檔案，以便開發「商務資料連接」\(BDC\) 服務的模型。  實體會描述資料欄位集合。  例如，實體可表示資料庫中的資料表。  方法會執行諸如加入、刪除或更新實體所代表的資料等工作。  如需詳細資訊，請參閱[將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## 加入實體  
 您可以將 \[**實體**\] 從 Visual Studio \[**工具箱**\] 拖曳或複製至 \[BDC 設計工具\] 上，以加入實體。  如需詳細資訊，請參閱[如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 在類別中定義實體的欄位。  例如，您可能會將名為 `Address` 的欄位加入至 `Customer` 類別。  您可以使用物件關聯式設計工具 \(O\/R 設計工具\) 等其他工具將新類別加入至專案，也可以使用現有的類別。  實體名稱與代表該實體的類別名稱不一定要相符。  當您在模型中定義方法時，可將類別與實體相關聯。  
  
## 加入方法  
 當使用者檢視、加入、更新或刪除清單中的資訊或以模型為基礎的 Web 組件時，BDC 服務會呼叫您模型中的方法。  您必須針對使用者可以執行的每項工作，將方法加入至模型。  從 \[**BDC 方法詳細資料**\] 視窗中選取任意五種基本方法型別，以便建立方法。  下表將描述 BDC 模型的五種基本方法。  
  
|方法|說明|  
|--------|--------|  
|搜尋工具|傳回實體執行個體的集合。  使用者開啟清單或 Web 組件時進行呼叫。  如需詳細資訊，請參閱[如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)。|  
|特定搜尋工具|傳回特定的實體執行個體。  使用者檢視清單中特定項目的詳細資料時進行呼叫。  如需詳細資訊，請參閱[如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)。|  
|建立者|將新資料加入至實體的資料來源。  Called when users choose the **New Item** button on the Ribbon of a list that is based on the model.  如需詳細資訊，請參閱[如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)。|  
|更新者|修改清單中的資料。  使用者更新清單中的資訊時進行呼叫。  如需詳細資訊，請參閱[如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)。|  
|刪除者|移除資料。  使用者從清單中刪除項目時進行呼叫。  如需詳細資訊，請參閱[如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。|  
  
## 定義方法參數  
 建立方法時，Visual Studio 會加入適合該方法型別的輸入和輸出參數。  這些參數只是替代符號。  在大部分情況下，您必須修改參數才能讓參數傳入或傳回正確的資料型別。  例如，根據預設，搜尋工具方法會傳回字串。  在大部分情況下，您要修改搜尋工具方法的傳回參數，以便其可以傳回實體集合。  為達此目的，您可以修改參數的型別描述元。  型別描述元是描述參數之資料型別的屬性集合。  如需詳細資訊，請參閱[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 Visual Studio 可讓您在模型中的參數之間複製型別描述元。  例如，您可能會針對 `GetCustomer` 方法的傳回參數定義名為 `CustomerTD` 的型別描述元。  您可以複製 \[**BDC 總管**\] 中的 `CustomerTD` 型別描述元，然後將該型別描述元貼入 `CreateCustomer` 方法的輸入參數中。  這可防止出現您不得不多次定義相同型別描述元的情況。  
  
##  <a name="MethodInstances"></a> 方法執行個體  
 建立方法時，Visual Studio 會加入預設方法執行個體。  方法執行個體是方法的參考，再加上參數的預設值。  單一方法可以具有多個方法執行個體。  每個執行個體都是方法簽章與一組預設值的組合。  如需詳細資訊，請參閱[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 執行專案時，方法執行個體會出現在 SharePoint 清單上方的下拉式清單中。  Users can choose method instances to view the data.  
  
 若要將預設值加入至方法執行個體，必須直接修改模型的 XML。  For more information, see [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## 加入篩選描述元  
 模型的消費者可能想要擷取符合某些準則之實體的執行個體。  若要啟用此功能，可以將篩選描述元加入至方法。  篩選描述元可讓模型消費者在執行方法前將值傳入方法，以便篩選方法結果集。  For more information, see [How to: Add Filter Parameters to Operations to Limit Instances from the External System](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint 提供可讓使用者提供篩選值的數種功能。  例如，「商務資料 Web 組件」會提供篩選文字方塊。  Users can limit the data in a list by entering a value in the text box.  如需如何將篩選描述元加入至方法的詳細資訊，請參閱 [如何：將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
### 篩選描述元屬性  
 您必須設定篩選描述元之 \[**關聯型別描述元**\]、\[**名稱**\] 和 \[**型別**\] 屬性的值。  所有其他屬性為選擇性的。  
  
 \[**關聯型別描述元**\] 屬性將篩選描述元與輸入參數相關聯。  當使用者提供篩選值時，BDC 服務會使用輸入參數將該值傳入方法中。  
  
 \[**型別**\] 屬性會描述您想要使用的篩選模式。  在 SharePoint 中，您所選取的篩選模式會影響出現在「使用者介面」\(UI\) 中的文字。  例如，若為「比較子」篩選模式，文字 \[**等於**\] 顯示為「商務資料 Web 組件」上方的控制項。  For more information about each filtering pattern, see [Types of Filters Supported by the BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 For more information about the properties of a filter descriptor, see [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### 提供預設值  
 在某些情況中，使用者可能不會提供篩選值。  您可以將預設值加入至方法執行個體，或者在方法的程式碼中設定預設值，來提供預設值。  For more information about how to add a default value to the method instance, see [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  如需如何在方法的程式碼中設定輸入參數預設值的範例，請參閱 [如何：將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
## 驗證模型  
 您可以在開發期間驗證模型。  Visual Studio 會識別阻止模型按預期運作的問題。  這些問題會出現在 Visual Studio \[**錯誤清單**\] 中。  
  
 You can validate a model by opening the shortcut menu for the BDC Designer and then choosing **Validate**.  If the model contains any errors, they appear in the **Error List**.  You can quickly move the cursor to the code that contains an error by double\-clicking the error in the list.  As an alternative, you can choose the F8 or Shift\+F8 keys repeatedly to step forward or backward through the errors in the list.  
  
 當以某種方式違反模型的規則時，便會發生驗證錯誤。  例如，如果將型別描述元的 \[**IsCollection**\] 屬性設定為 **true**，但是不存在子型別描述元，則會出現驗證錯誤。  您可能需要參考 BDC 模型的規則，來了解 Visual Studio \[**錯誤清單**\] 中所出現的某些錯誤。  For more information about the rules of a BDC model, see [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## 對包含模型的方案進行偵錯  
 您可以偵錯程式碼，其方式就像偵錯任何 Visual Studio 中的程式碼一樣。  若要對程式碼進行偵錯，在您的程式碼中的任意位置設定中斷點，然後啟動偵錯工具。  Visual Studio 便會開啟 SharePoint 網站。  在 SharePoint 中，建立使用商務資料的清單或 Web 組件。  接著，您便可以逐步執行程式碼。  如需偵錯 SharePoint 專案的詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
 您也可以對加入至專案的自訂組件，進行其程式碼的偵錯。  但若要對自訂組件中的程式碼進行偵錯，您必須將該組件加入至方案套件。  如需詳細資訊，請參閱[如何：新增與移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 如需將自訂組件加入至專案的詳細資訊，請參閱 [如何：在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)。  
  
### 設定 BDC 安全性  
 在可以對方案進行偵錯之前，您可能需要修改 SharePoint 中的安全性設定。  若要修改這些設定，請在「SharePoint 2010 管理中心」網站中開啟「商務資料連接服務應用程式」。  在 \[**設定中繼資料存放區使用權限**\] 對話方塊中加入您的使用者帳戶，然後選取下列任何一個選項：  
  
|工作|選項|  
|--------|--------|  
|將模型部署至 BDC 服務。|Edit|  
|使用模型中的外部內容類型 \(實體\) 來建立清單和 Web 組件。|用戶端中的可選取項目|  
|建立、讀取、更新和刪除實體資料。|執行|  
  
 For more information about these settings, see [Business Data Connectivity service management](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 您也可以為個別模型或外部內容類型設定安全性權限。  For more information about how to set the security permissions of a model, see [BDC model management](http://go.microsoft.com/fwlink/?LinkID=178884).  For more information about how to set the security permissions of an external content type, see [External content type management](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  使用這些設定來對您本機 SharePoint 伺服器上的方案進行偵錯。  For more information about how to configure BDC\-related security settings on production SharePoint server, see [Business Data Connectivity Services security overview](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### 撤銷損毀的模型  
 The first time that you start the debugger, Visual Studio deploys the entire model to SharePoint.  之後每次啟動偵錯工具時，Visual Studio 都會以您在部署之間所進行的變更來更新 SharePoint 中的模型。  
  
 有時候您可能想讓 Visual Studio 從 SharePoint 完全撤銷模型。  例如，模型已損毀。若要將模型重新部署至 SharePoint，請將模型的 \[**累加式更新**\] 屬性設定為 \[**False**\]，然後啟動偵錯工具。  當您選取 \[**BDC 總管**\] 中代表模型的節點時，\[**累加式更新**\] 屬性便會出現在 \[**屬性**\] 視窗中。  根據預設，模型的名稱為 \[**BdcModel1**\]。  
  
### 變更模型中實體的識別碼名稱  
 如果您在部署模型後變更識別碼的名稱，您可能會看見部署錯誤。  將模型的 \[**累加式更新**\] 屬性變更為 \[**False**\]，並無法解決此錯誤。  您必須手動撤銷模型，然後重新部署方案。  如需詳細資訊，請參閱[SharePoint 方案疑難排解](../sharepoint/troubleshooting-sharepoint-solutions.md)。  您可以在首次部署模型前將 \[**累加式更新**\] 屬性變更為 \[**False**\]，以避免此錯誤。  
  
## 尋找 BDC 模型項目文件  
 Visual Studio 會針對每個實體、方法或您建立的其他項目，將 XML 元素加入至模型。  項目屬性 \(Attribute\) 會做為屬性 \(Property\) 顯示在 \[**屬性**\] \(Property\) 視窗中。  For information about the elements and attributes that Visual Studio generates as you design the model, see [BDCMetadata Schema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## 相關主題  
  
|標題|說明|  
|--------|--------|  
|[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)|描述可讓您使用視覺化方式設計 BDC 模型的工具。|  
|[如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)|示範如何將外部內容類型或實體加入至模型。|  
|[如何：加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)|示範如何加入可讓使用者檢視清單或 Web 組件中實體清單的方法。|  
|[如何：加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)|示範如何加入可讓使用者檢視特定實體詳細資料的方法。|  
|[如何：加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)|示範如何加入可讓使用者將記錄直接從清單或 Web 組件加入至資料來源的方法。|  
|[如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)|示範如何加入可讓使用者使用清單或 Web 組件之使用者介面 \(UI\) 中的選項，以便從資料來源移除資料的方法。|  
|[如何：加入更新者方法](../sharepoint/how-to-add-an-updater-method.md)|示範如何加入可讓使用者直接從清單或 Web 組件變更資料來源中資料記錄的方法。|  
|[如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)|示範如何使用 Visual Studio 中的「方法詳細資料視窗」，將輸入和傳回參數加入至方法。|  
|[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|示範如何定義模型中的參數資料型別。|  
|[如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)|示範如何建立 BDC 所執行方法的執行個體。|  
|[如何：將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|示範如何讓使用者限制搜尋工具方法所傳回執行個體的數目。|  
|[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)|描述如何定義模型中實體之間的關係。  「商務資料 Web 組件」、「外部清單」和自訂應用程式可以在使用者介面 \(UI\) 中顯示這些資料關係。|  
|[如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)|示範如何定義模型中實體之間的關係。|  
|[逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|提供示範如何建立和測試在 SharePoint 外部清單中顯示連絡資訊之模型的逐步指示。|  
|[將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|提供建立和設計 BDC 服務模型的概觀。|  
  
  