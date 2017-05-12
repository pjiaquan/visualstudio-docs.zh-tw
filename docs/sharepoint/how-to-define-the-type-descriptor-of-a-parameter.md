---
title: "How to: Define the Type Descriptor of a Parameter"
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
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  類型描述元包含描述參數資料類型的屬性。  類型描述元可以定義欄位、實體或實體集合。  如需詳細資訊，請參閱 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### 定義參數的類型描述元  
  
1.  在 \[BDC 方法詳細資料\] 視窗中，選擇此參數的類型描述元。  
  
2.  在功能表上選擇 \[檢視\]、\[屬性視窗\]。  
  
3.  在 \[屬性\] 視窗中設定類型描述元的屬性。  
  
     下列程序描述如何將類型描述元定義為欄位、實體或實體集合。  
  
### 定義欄位  
  
1.  在 \[屬性\] 視窗中，將類型描述元的 \[名稱\] 屬性設定為類型中代表實體的欄位名稱 \(例如：FirstName\)。  
  
2.  在 \[TypeName\] 屬性旁邊的清單中，選取適當的資料類型 \(例如 \[Int32\]\)。  
  
     如需其他選擇性參數的詳細資訊，請參閱 [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx)。  
  
### 定義實體  
  
1.  在 \[屬性\] 視窗中，將 \[名稱\] 屬性設定為描述實體的名稱 \(例如：Contact\)。  
  
2.  將 \[TypeName\] 屬性設定為代表實體類型的完整名稱。  此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。  
  
    -   對於您專案中的類別，選擇 \[TypeName\] 旁邊的向下箭號，在出現的對話方塊中選擇 \[目前的專案\] 標籤，然後選擇專案中的類別。  
  
         完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。  下列範例會將 \[TypeName\] 屬性值設定為您專案中的類別。  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。  
  
         下列範例會將 \[TypeName\] 屬性值設定為您在方案中參考之組件中定義的類型。  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   若為 BDC 物件模型中定義的類型，完整名稱包含該類型的命名空間和名稱。  
  
         下列範例會將 \[TypeName\] 屬性值設定為 BDC 物件模型中的類型。  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  在 \[BDC 方法詳細資料\] 視窗中，開啟針對類型描述元而顯示的下拉式清單，然後選擇 \[編輯\]。  
  
     \[BDC 總管\] 視窗隨即開啟。  
  
4.  在 \[BDC 總管\] 中，開啟類型描述元的捷徑功能表，然後選擇 \[加入類型描述元\]。  
  
     新的類型描述元便會做為子類型描述元加入至實體類型描述元。  將此類型描述元設定為欄位。  
  
5.  重複步驟 4，為該實體的每個欄位加入子類型描述元。  
  
### 定義實體集合  
  
1.  在 \[BDC 方法詳細資料\] 視窗中，選取您所需參數的類型描述元。  
  
2.  在功能表上選擇 \[檢視\]、\[屬性視窗\]。  
  
3.  在 \[屬性\] 視窗中，將 \[名稱\] 屬性設定為描述此實體的名稱 \(例如：Contacts\)。  
  
4.  將 \[IsCollection\] 屬性設定為 **True**。  這表示此類型描述元是實體的集合。  
  
5.  將 \[TypeName\] 屬性設定為包含 <xref:System.Collections.Generic.IEnumerable%601> 介面參考的字串，並設定代表實體之類型的完整名稱。  此類型可以是您專案中的類別、您在方案中所參考組件中定義的類型或 BDC 物件模型中定義的類型。  
  
    -   對於您專案中的類別，選擇 \[TypeName\] 旁邊的向下箭號，在出現的對話方塊中選擇 \[目前的專案\] 標籤，然後選擇專案中的類別。  
  
         完整名稱包含類別的命名空間和名稱，後面跟有 LOB 系統的名稱。  
  
         下列範例會將 \[TypeName\] 屬性值設定為您專案中的類別集合。  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   若為位於您方案之組件中的類型，完整名稱包含類型的名稱、組件的名稱、版本號碼、文化特性和公開金鑰語彙基元。  
  
         下列範例會將 \[TypeName\] 屬性值設定為您在方案中參考之組件中的類型集合。  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   若為 BDC 物件模型中定義的類型，完整名稱僅包含該類型的命名空間和名稱。  
  
         下列範例會將 \[TypeName\] 屬性值設定為 BDC 物件模型中定義的類型集合。  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  在 \[BDC 方法詳細資料\] 視窗中，開啟針對類型描述元而顯示的下拉式清單，然後選擇 \[編輯\]。  
  
     \[BDC 總管\] 視窗隨即開啟。  
  
7.  在 \[BDC 總管\] 中，開啟類型描述元的捷徑功能表，然後選擇 \[加入類型描述元\]。  
  
     新的類型描述元便會做為子類型描述元加入集合類型描述元。  將此類型描述元設定為實體。  
  
## 請參閱  
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)   
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  