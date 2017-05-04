---
title: "逐步解說：建立 SharePoint 的網站資料行、內容類型和清單 | Microsoft Docs"
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
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 內容類型"
  - "Visual Studio 中的 SharePoint 開發, 欄位"
  - "Visual Studio 中的 SharePoint 開發, 清單定義"
  - "Visual Studio 中的 SharePoint 開發, 清單執行個體"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 逐步解說：建立 SharePoint 的網站資料行、內容類型和清單
  下列程序示範如何建立自訂 SharePoint 網站欄 \(或 *欄位*\) 以及做為使用網站欄的內容類型。  它也會示範如何建立使用新內容類型的清單。  
  
 本逐步解說包含下列工作：  
  
-   [建立自訂網站欄](#BKMK_CreatingCustSiteCols)。  
  
-   [建立自訂內容類型](#BKMK_CreateCustContType)。  
  
-   [建立清單](#BKMK_CreateList)。  
  
-   [建立清單](#BKMK_CreateList)。  
  
-   [測試應用程式](#BKMK_TestApp)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Windows 和 SharePoint 版本。  如需詳細資訊，請參閱[開發 SharePoint 方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> 建立自訂網站欄  
 這個範例建立醫院中處理患者的清單。  首先，您必須在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中建立 SharePoint 專案並加入網站欄，如下所示。  
  
#### 若要建立專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \[**檔案**\] 功能表上，選擇 \[**新增**\]、\[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下的 \[**SharePoint**\] 節點，再按一下 \[**2010**\]。  
  
3.  在 \[**範本**\] 窗格中，選擇 \[**SharePoint 2010 專案**\]，將名稱改為 Clinic，然後選擇 \[**確定**\] 按鈕。  
  
     SharePoint 2010 專案範本是空專案，在這個範例中用來包含網站欄和之後要加入的其他專案項目。  
  
4.  在 \[**指定網站和安全性層級進行偵錯**\] 頁面上，輸入您想要加入新自訂欄位項目之本機 SharePoint 網站的 URL，或使用預設位置 \(`http://<`*SystemName*`>/)`\)。  
  
5.  在 \[**此 SharePoint 方案的信任層級為何?**\] 區段中，使用 \[**部署為沙箱化方案**\] 預設值。  
  
     如需沙箱化方案與陣列方案比較的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
6.  選擇 \[**完成**\] 按鈕。  在 \[**方案總管**\] 現在應該列出專案。  
  
#### 若要加入網站欄  
  
1.  加入新網站欄。  若要這麼做，請在 \[**方案總管**\] 中，開啟 \[**Clinic**\] 的捷徑功能表，然後選擇 \[**加入**\]、\[**新增項目**\]。  
  
2.  在 \[**加入新項目。**\] 對話方塊中，選取 \[**網站資料欄**\]，將名稱改為 Patient Name，然後按 \[**加入**\] 按鈕。  
  
3.  在網站欄的 Elements.xml 檔案中，請將 \[**類型**\] 設定保留為 \[**文字**\]，並將 \[**群組**\] 設定變更為診斷網站欄。  完成後，網站欄的 Elements.xml 檔案應該看起來與下列範例相同。  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  使用相同的程序，再將兩個網站資料行加入至專案：Patient ID \(型別為 Integer\) 和 Doctor Name \(型別為 Text\)。  將其群組值設定為診斷網站欄。  
  
##  <a name="BKMK_CreateCustContType"></a> 建立自訂內容類型  
 接下來，建立以連絡人內容型別為基礎的內容類型，其包含您在先前程序中建立的網站欄。  將一個內容類型建立在現有內容類型之上，可以節省時間，因為這個基底內容類型可以提供數個網站欄，供新的內容類型使用。  
  
#### 若要建立自訂內容類型  
  
1.  將內容類型加入至專案。  若要這麼做，請在 \[**方案總管**\] 中選擇專案節點。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
4.  在 \[**範本**\] 窗格中，選取 \[**內容類型**\] 範本，將名稱變更為 Patient Info，然後選擇 \[**加入**\] 按鈕。  
  
     \[**SharePoint 自訂精靈**\] 隨即開啟。  
  
5.  在 \[**這個內容類型因繼承自哪個基底內容類型**\] 清單中，選取 \[**連絡人**\] 做為根據新內容類型的內容類型，然後選擇 \[**結束**\] 按鈕。  
  
     這麼做可讓您在連絡人內容類型存取其他可能有用的網站欄，除了您先前定義的網站欄之外。  
  
6.  在內容型別設計工具出現後，在 \[**資料行**\] 索引標籤中，加入先前定義的三個網站欄： \[**Patient Name**\]、 \[**Patient ID**\] 和 \[**Doctor Name**\]。  若要加入這些資料行，請在 \[**顯示名稱**\] 下選取網站欄清單的第一個清單方塊，然後在清單中一次選取一個網站欄。  
  
    > [!TIP]  
    >  若要快速選取網站欄，請輸入資料行名稱的前幾個字母來篩選清單。  
  
7.  除了三個自訂網站欄以外，從網站欄清單中加入 \[**註解**\] 網站欄。  
  
8.  選取 \[**需要**\] 核取方塊，讓 \[**Patient Name**\] 和 \[**Patient ID**\] 網站欄成為必要欄位。  
  
9. 在 \[**內容類型**\] 索引標籤上，確認此內容類型的名稱是 \[**Patient Info**\]，然後變更描述為 Patient information card。  
  
10. 將 \[**群組名稱**\] 變更為診斷內容類型，保留其他設定的預設值。  
  
11. 在功能表列上，選擇 \[**檔案**\]、\[**全部儲存**\]，然後關閉內容型別的設計工具。  
  
##  <a name="BKMK_CreateList"></a> 建立清單  
 現在，建立使用新內容類型和網站欄的清單。  
  
#### 若要建立清單  
  
1.  加入清單至專案  若要這麼做，請在 \[**方案總管**\] 中選擇專案節點。  
  
2.  在功能表列中，選擇 \[**專案**\]、\[**加入新項目**\]。  
  
3.  在 \[**Visual C\#**\] 或 \[**Visual Basic**\] 底下，展開 \[**SharePoint**\] 節點，然後選擇 \[**2010**\] 節點。  
  
4.  在 \[**範本**\] 窗格中，選取 \[**清單**\] 範本，將名稱變更為 Patients，然後選擇 \[**加入**\] 按鈕。  
  
5.  保留設定為 \[**預設 \(空白\)**\] 的 \[**自訂架構的清單**\]，然後選擇 \[**結束**\] 按鈕。  
  
6.  在清單設計工具中，選擇 \[**內容類型**\] 按鈕以顯示 \[**內容類型設定**\] 對話方塊。  
  
7.  選取新的資料列，在內容類型的清單中選取 \[**Patient Info**\] 內容類型，然後選擇 \[**確定**\] 按鈕。  
  
     這樣做會將所有網站欄從 \[**Patient Info**\] 內容類型加入至清單。  
  
8.  刪除所有清單中的網站欄，除了下列：  
  
    -   Patient ID  
  
    -   Patient Name  
  
    -   Home Phone  
  
    -   E\-Mail  
  
    -   Doctor Name  
  
    -   註解  
  
9. 在 \[**資料行的顯示名稱**\] 底下，選取空白資料列、加入自訂清單資料行，並將其命名為 Hospital。  保留其資料型別為 \[**單一文字行**\]。  
  
     自訂清單網站欄只套用至這個清單。  當您將自訂清單資料行加入至清單時，新的清單內容類型 \(包括所有加入至清單的資料欄\) 已建立並且其設定同預設清單。  
  
    > [!TIP]  
    >  如果您從網站欄清單中選取資料行，則已使用現有的網站欄。  不過，如果您輸入名稱值，而非在清單中選取任何資料列，仍會建立一個自訂清單資料行，即使具有相同名稱的資料行清單中已存在。  
  
     或者，與其設定自訂清單資料行的資料型別設定為 \[**單行文字**\]，您可以選擇將這個資料行的資料型別設定為 \[搜尋\]，如此它的值會是擷取自資料表或其他清單。  如需搜尋資料的詳細資訊，請參閱 [SharePoint 2010 的清單關係](http://go.microsoft.com/fwlink/?LinkId=224994) 和 [搜尋和清單關係](http://go.microsoft.com/fwlink/?LinkID=224995)。  
  
10. 在 \[**Patient ID**\] 和 \[**Patient Name**\] 方塊旁，請選取 \[**需要**\] 核取方塊。  
  
11. 在 \[**檢視**\] 索引標籤中，選取空白行建立檢視。  輸入病患詳細資料。  
  
     在 \[**檢視**\] 索引標籤上，您可以指定要出現在 SharePoint 清單的資料行。  
  
12. 選取新的 \[**Patient Details**\] 資料行，然後選擇 \[**設定為預設值**\] 按鈕。  
  
     新檢視現在是清單的預設檢視。  
  
13. 將下列資料行依照下列順序加入至 \[**選取的資料行**\] 清單：  
  
    -   Patient ID  
  
    -   Patient Name  
  
    -   Home Phone  
  
    -   E\-Mail  
  
    -   Doctor Name  
  
    -   Hospital  
  
    -   註解  
  
14. 在 \[**屬性**\] 清單中，選取 \[**排序和群組**\] 屬性，然後選擇省略符號按鈕 ![省略符號圖示](../sharepoint/media/ellipsisicon.png "省略符號圖示") 以顯示 \[**排序和群組**\] 對話方塊。  
  
15. 在 \[**資料行名稱**\] 清單中，選取 \[**Patient Name**\]，確定 \[**排序**\] 資料行設為 \[**Ascending**\]，然後選擇 \[**確定**\] 按鈕。  
  
##  <a name="BKMK_TestApp"></a> 測試應用程式  
 現在這個自訂網站欄、內容類型和清單已經就緒，請將它們部署至 SharePoint，並執行應用程式來測試它。  
  
#### 若要測試應用程式  
  
1.  在功能表列上，選擇 \[**檔案**\]、\[**全部儲存**\]。  
  
2.  選擇 F5 鍵以執行應用程式。  
  
     應用程式已編譯，它的功能已部署至 SharePoint 並啟動。  
  
3.  在快速巡覽列，請選擇 \[**Patients**\] 連結顯示 \[**Patients**\] 清單。  
  
     在清單中的資料行名稱應符合您在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的 \[**檢視**\] 索引標籤輸入的內容。  
  
4.  選擇 \[**加入新項目**\] 連結建立一個病患資訊卡。  
  
5.  輸入資訊至欄位中，然後選取 \[**儲存**\] 按鈕。  
  
     新的紀錄就會出現在清單中。  
  
## 請參閱  
 [建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [如何建立自訂欄位型別](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [內容類型](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columns](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  