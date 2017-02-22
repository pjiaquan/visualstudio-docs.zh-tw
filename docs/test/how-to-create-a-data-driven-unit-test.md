---
title: "如何：建立資料驅動型單元測試 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "單元測試，執行"
  - "單元測試，資料驅動"
  - "資料驅動的單元測試"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# 如何：建立資料驅動型單元測試
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用Microsoft 單元測試架構的Managed 程式碼，您可以設定單元測試方法來從資料來源擷取用來測試方法的值。  這個方法會在資料來源中每個資料列依序執行，可讓您輕鬆地使用單一方法測試各種輸入。  
  
 此主題包括下列章節：  
  
-   [待測方法](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [建立資料來源](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [加入 TestContext 至測試類別](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [寫入測試方法](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [指定 DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [使用 TestContext.DataRow 存取的資料。](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [執行測試並檢視結果](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 建立資料驅動型單元測試包括下列步驟:  
  
1.  建立包含您在測試方法使用的值的資料來源。  資料來源可以是任何在機器上登錄執行測試的型別。  
  
2.  加入私用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 欄位和公用 `TestContext` 屬性來測試類別。  
  
3.  建立單元測試方法並加入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 屬性加入其中。  
  
4.  使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> 索引子屬性擷取您在測試中使用的值。  
  
##  <a name="BKMK_The_method_under_test"></a> 待測方法  
 例如，假設我們已經建立:  
  
1.  `MyBank` 會接受並處理序帳戶不同類型的交易。  
  
2.  在`MyBank` 的一個叫做 `BankDb` 的專案負責管理帳號交易。  
  
3.  一個叫做`Maths`存在於 `DbBank`的專案會處理數學函式來確保所有交易都是對銀行有利的。  
  
4.  一個叫做 `BankDbTests` 的單元測試專案來測試 `BankDb` 元件的行為。  
  
5.  一個叫做 `MathsTests` 的單元測試專案來驗證 `Maths` 類別的行為。  
  
 我們將用迴圈加入兩個整數來測試一個在`Maths` 的方法:  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> 建立資料來源  
 若要測試 `AddIntegers` 方法，我們會建立指定參數的範圍值和總和以及自己所傳回的資料來源。  在我們的範例中，我們會建立名為 `MathsData`的SQL Compact 資料庫和名為 `AddIntegersData` 的包含下列資料行名稱和值的資料表  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> 加入 TestContext 至測試類別  
 單元測試架構建立 `TestContext` 物件儲存資料驅動型測試的資料來源資訊。   架構會將這個物件做為 `TestContext` 我們建立的屬性值。  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 在測試方法中，您可以透過 `DataRow`的`TestContext`索引屬性來存取資料。  
  
##  <a name="BKMK_Writing_the_test_method"></a> 寫入測試方法  
 `AddIntegers` 的測試方法相當簡單。   對於資料來源中的每個資料列，我們會使用 **FirstNumber** 和 **SecondNumber** 資料行值的 `AddIntegers` 做為參數，因此，我們檢查傳回值是否為 **總和。** 資料行值:  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 請注意 `Assert` 方法包括顯示已失敗的反覆項目的 `x` 和 `y` 值中的訊息。   根據預設，已確定的值， `expected` 和 `actual`，已包含在為失敗的測試的詳細資料。  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> 指定 DataSourceAttribute  
 `DataSource` 屬性對資料來源和您在測試方法使用的資料表名稱指定連接字串。   連接字串中的確切資訊會因您所使用的資料來源種類而有所不同。  在此範例中，我們使用了 SqlServerCe 資料庫。  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 資料來源屬性有三個建構函式。  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 具有參數的建構函式在方案中使用 app.config 檔案中儲存的連接資訊。  *dataSourceSettingsName* 是 XML 項目的名稱已在指定連接資訊的組態檔的。  
  
 使用 app.config 檔可讓您變更資料來源中的位置，而不需要對單元測試做變更。  如需如何建立和使用 app.config 檔案的詳細資訊，請參閱[逐步解說：使用組態檔定義資料來源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 具有兩個參數的 `DataSource` 建構函式 \(Constructor\) 為資料來源和包含的資料可用來測試方法資料表名稱指定連接字串。  
  
 連接字串是根據資料來源的型別，不過，它應該包含指定資料提供者的非變異的提供者名稱的項目。  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> 使用 TestContext.DataRow 存取的資料。  
 若要存取在 `AddIntegersData` 資料的資料表，請使用 `TestContext.DataRow` 索引子。   `DataRow` 是<xref:System.Data.DataRow> 物件，因此，我們以索引或資料行名稱擷取資料行值。  因為值傳回為物件，我們必須將它們轉換為適當的型別:  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> 執行測試並檢視結果  
 當您完成撰寫測試方法時，建立測試專案。   測試方法都會位於 \[**未執行的測試**\] 群組中的測試總管視窗。  您執行，撰寫，並重新執行測試、測試總管中顯示結果。 \[**失敗的測試**\] 的群組中， \[**通過的測試**\] 和 \[**未執行的測試**\]。   您可以選擇 **全部執行** 執行所有測試，或選取 **執行** 選取測試的子集執行。  
  
 測試結果列在 \[總管\] 頂端的動畫為測試回合。  在測試回合結束時，所有測試都通過的話狀態列會是綠色的，如果有任何測試失敗則為紅色。  測試回合的摘要出現在詳細資料窗格中的測試總管視窗底部。  選取測試並下方窗格中的測試詳細資料。  
  
 如果您執行在我們的範例中的方法， `AddIntegers_FromDataSourceTest` 結果列會變成紅色，並測試方法移至 \[**失敗的測試**\] A 資料驅動型測試失敗，如果有任何資料來源中的重複的方法會失敗。  當您選取測試總管視窗中的失敗的資料驅動型測試，詳細資料窗格會顯示資料列索引所識別的每個反覆項目的結果。  在範例中，會出現 `AddIntegers` 演算法無法正確處理負值。  
  
 當修正待測方法和重新執行測試時，結果列空轉綠色，而測試方法移至 \[**成功的測試**\] 群組。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [How to: Create and Run a Unit Test](http://msdn.microsoft.com/zh-tw/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [對程式碼進行單元測試](../test/unit-test-your-code.md)   
 [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)   
 [使用適用於 Managed 程式碼的 Microsoft 單元測試架構撰寫適用於 .NET Framework 的單元測試](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)