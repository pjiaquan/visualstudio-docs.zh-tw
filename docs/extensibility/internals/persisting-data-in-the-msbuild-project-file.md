---
title: "在 MSBuild 專案檔案中保存的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案檔，保存中的資料"
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 在 MSBuild 專案檔案中保存的資料
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案子類型可能需要將子型別特定資料保存到專案檔，以供日後使用。  專案子類型會使用專案檔案的持續性，來符合下列需求：  
  
1.  保存資料做為建置專案的一部分。  \(如需有關 Microsoft 建置引擎的詳細資訊，請參閱[MSBuild](http://msdn.microsoft.com/zh-tw/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)。\) 可以與組建相關的資訊：  
  
    1.  組態無關的資料。  也就是儲存在 MSBuild 含有空白或遺漏的條件的項目中的資料。  
  
    2.  組態相關的資料。  也就是儲存在特定的專案組態所容許的 MSBuild 項目中的資料。  例如：  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  保存不建置相關的資料。  這項資料，都可以自由格式不會針對 XML 結構描述進行驗證的 xml 表示。  
  
    1.  組態無關的資料。  
  
    2.  組態相關的資料。  
  
## 保存與組建相關的資訊  
 持續性資料適用於建置專案的工作被透過 MSBuild。  MSBuild 系統維謢與組建相關的資訊的主要資料表。  專案子類型有責任存取這份資料來取得及設定屬性值。  專案子類型也可擴大組建相關的資料表格，藉由新增其他屬性，以保存及移除屬性，因此不會保存。  
  
 若要修改的 MSBuild 資料，專案子類型負責 MSBuild 屬性物件擷取基本的專案系統透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>已實作的介面上核心專案系統和彙總的專案子類型查詢對它執行`QueryInterface`。  
  
 下列程序會說明的步驟來移除屬性，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  
  
#### 若要移除 MSBuild 專案檔中的屬性  
  
1.  呼叫`QueryInterface`的<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>的專案子類型。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>與`pszPropName`設定為 \[您想要移除的屬性。  
  
### 保存非組建相關的資訊  
 持續性的專案檔案中建立並不重要的資料透過<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>。  
  
 您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>在`project subtype aggregator`物件， `project subtype project configuration`物件，或兩者。  
  
 下列各點概述有關非組建的相關資訊的持續性的主要概念。  
  
-   基底專案呼叫之主要專案子類型 \(也就是最外層的專案子類型\) 彙總物件載入和儲存組態無關的資料，並呼叫專案子類型的專案組態的物件載入或儲存組態相依的資料。  
  
-   基底專案呼叫類別的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>多細的專案子類型彙總，每一個層級，並將每個層級的 GUID。  
  
-   基底的專案會傳遞或接收 XML 片段，專門用於特定專案的子型別，並使用這項機制，這種彙總層級之間的保存狀態。  
  
-   基底的專案會呼叫最外層的專案子類型的<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>將 GUID 傳入的實作。  GUID 是屬於最外層的專案子類型，它會處理呼叫本身。 否則就會委派呼叫至內部的專案子類型，依此類推，直到找到 GUID 對應至的專案子類型。  
  
-   專案子型別也可以修改 XML 片段之前或之後它會委派呼叫給內部的專案子類型。  下列範例摘錄自專案檔，其中包含專案子類型的特定屬性的檔案名稱傳遞給該專案子類型。  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## 請參閱  
 [專案子類型](../../extensibility/internals/project-subtypes.md)