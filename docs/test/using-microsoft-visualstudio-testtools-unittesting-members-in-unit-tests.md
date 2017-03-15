---
title: "在單元測試中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成員 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# 在單元測試中使用 Microsoft.VisualStudio.TestTools.UnitTesting 成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

單元測試架構可以支援 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的單元測試。  當您撰寫單元測試的程式碼時，請使用 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework> 命名空間中的類別 \(Class\) 和成員。  不論從頭開始撰寫單元測試，或是修改從受測程式碼所產生的單元測試時，都可以使用這些類別和成員。  
  
## 項目群組  
 為了協助提供更清楚的單元測試架構概觀，本章節會將 UnitTesting 命名空間的項目以相關功能進行分組。  
  
> [!NOTE]
>  屬性項目 \(以 Attribute 字串結束\) 可以選擇是否搭配 Attribute 字串使用。  例如，下列兩行範例程式碼的作用完全相同：  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### 用於資料驅動型測試的項目  
 請使用下列項目設定資料驅動型單元測試。  如需詳細資訊，請參閱[如何：建立資料驅動型單元測試](../test/how-to-create-a-data-driven-unit-test.md)與[逐步解說：使用組態檔定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## 用於建立呼叫順序的屬性  
 具有下列屬性之一的程式碼項目會在您所指定的時刻被呼叫。  如需詳細資訊，請參閱[Anatomy of a Unit Test](http://msdn.microsoft.com/zh-tw/a03d1ee7-9999-4e7c-85df-7d9073976144)。  
  
### 針對組件  
 在組件 \(Assembly\) 載入之後和卸載之前，都會立即呼叫 AssemblyInitialize 和 AssemblyCleanup。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### 針對類別  
 在類別載入之後和卸載之前，都會立即呼叫 ClassInitialize 和 ClassCleanup。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### 針對測試方法  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## 用來識別測試類別和方法的屬性  
 每個測試類別都必須具有 TestClass 屬性，而且每個測試方法都必須具有 TestMethod 屬性。  如需詳細資訊，請參閱[Anatomy of a Unit Test](http://msdn.microsoft.com/zh-tw/a03d1ee7-9999-4e7c-85df-7d9073976144)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Assert 類別和相關的例外狀況  
 單元測試可以使用各種 Assert 陳述式、例外狀況和屬性，確認特定的應用程式行為。  如需詳細資訊，請參閱[使用 Assert 類別](../test/using-the-assert-classes.md)。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## TestContext 類別  
 下列屬性及指派給這些屬性的值，都會出現在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 \[屬性\] 視窗中，供特定測試方法使用。  這些屬性並非由單元測試的程式碼存取。  而是要影響單元測試的使用或執行方式 \(透過 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 IDE 或是由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 測試引擎進行\)。例如，這些屬性中的某些屬性會顯示成 \[測試管理員\] 視窗和 \[測試結果\] 視窗中的資料行，這表示您可以使用這些屬性來分組及排序測試和測試結果。  TestPropertyAttribute 就是這種屬性，可以用來將任意的中繼資料加入至單元測試。  例如，以 `[TestProperty("TestPass", "Accessibility")]` 標記單元測試，即可使用此屬性儲存這項測試所涵蓋之成功測試的名稱。  或是，您可以使用它來儲存測試類型的指示器：`[TestProperty("TestKind", "Localization")]`。  使用這個屬性 \(Attribute\) 所建立的屬性 \(Property\)，以及您所指派的屬性值 \(Property Value\)，都會在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \[屬性\] 視窗的 \[**測試專屬**\] 標題下出現。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## 測試組態類別  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## 用於產生報告的屬性  
 本節中的屬性 \(Attribute\) 會將其所附加的測試方法，與 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] Team 專案之專案階層架構中的實體 \(Entity\) 相關聯。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## 搭配私用存取子使用的類別  
 如[Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/zh-tw/2056c6a7-6672-42a7-8f53-fead33c56deb)所說明，您可以產生私用方法的單元測試。  這項產生作業會建立一個私用存取子類別，該類別則會具現化 \(Instantiate\) PrivateObject 類別的物件。  PrivateObject 類別是一種包裝函式類別 \(Wrapper Class\)，會使用反映 \(Reflection\) 做為私用存取子處理序的一部分。  PrivateType 類別也與此相似，不過是用來呼叫私用靜態方法，而非私用執行個體方法。  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>