---
title: "樣板參數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目範本, 參數"
  - "專案範本, 參數"
  - "範本參數 [Visual Studio]"
  - "Visual Studio 範本, 參數"
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 樣板參數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用範本中的參數，當範本具現化時，您可以取代範本的主要部分的值，例如類別名稱和命名空間。  當使用者在 \[**新增專案**\] 或 \[**加入新項目**\] 對話方塊中按一下 \[**確定**\] 時，在背景中執行的範本精靈將會取代這些參數。  
  
## 宣告和啟用範本參數  
 範本參數是以 $*parameter*$ 格式宣告。  例如：  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### 若要啟用範本中的參數替換  
  
1.  在範本的 .vstemplate 檔中，找出與您要啟用參數替換之項目相對應的 `ProjectItem` 項目。  
  
2.  將 `ProjectItem` 項目的 `ReplaceParameters` 屬性 \(Attribute\) 設定為 `true`。  
  
3.  在專案項目的程式碼檔案中，在適當的位置加入參數。  例如，下列參數指定 safeprojectname 用於某一檔案中的命令空間：  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## 保留的範本參數  
 下表列出了保留的範本參數，它們可供任何範本使用：  
  
> [!NOTE]
>  範本參數是區分大小寫的。  
  
|參數|描述|  
|--------|--------|  
|`clrversion`|目前版本的 Common Language Runtime \(CLR\)。|  
|`GUID [1-10]`|GUID，用來取代專案檔的專案 GUID。  您最多可以指定 10 個唯一 GUID \(例如 `guid1)`。|  
|`itemname`|使用者在**加入新項目**對話方塊中提供的名稱。|  
|`machinename`|目前的電腦名稱 \(例如 Computer01\)。|  
|`projectname`|使用者在**新增專案**對話方塊中提供的名稱。|  
|`registeredorganization`|來自 HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\RegisteredOrganization 的登錄機碼 \(Registry Key\) 值。|  
|`rootnamespace`|目前專案的根命名空間。  這個參數只適用於項目範本。|  
|`safeitemname`|使用者在 \[**加入新項目**\] 對話方塊中提供的名稱，但名稱中所有的 Unsafe 字元和空格都已刪除。|  
|`safeprojectname`|使用者在 \[**新增專案**\] 對話方塊中提供的名稱，但名稱中所有的 Unsafe 字元和空格都已刪除。|  
|`time`|目前時間，其格式為 DD\/MM\/YYYY 00:00:00。|  
|`SpecificSolutionName`|方案的名稱。  當「建立方案目錄」已核取時， `SpecificSolutionName` 有方案名稱。  當「建立方案目錄」沒有被檢查， `SpecificSolutionName` 是空白的。|  
|`userdomain`|目前使用者的網域。|  
|`username`|目前使用者的名稱。|  
|`webnamespace`|目前網站的名稱。  這個參數使用於 Web 表單範本中，以確保類別名稱是唯一的。  如果網站位於 Web 伺服器的根目錄，則這個範本參數會解析至 Web 伺服器的根目錄。|  
|`year`|目前年份，其格式為 YYYY。|  
  
## 自訂範本參數  
 除了參數替換期間將會自動使用保留的範本參數，您還可以指定自己的範本參數和值。如需詳細資訊，請參閱[CustomParameters 項目 \(Visual Studio 範本\)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## 範例：取代檔名  
 您可以使用具有 `TargetFileName` 屬性的參數，為專案項目指定可變的檔名。  例如，您可以指定 .exe 檔使用專案名稱做為檔案名稱，而且此專案名稱是由 `$projectname$` 指定。  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## 範例：使用專案名稱做為命名空間名稱  
 若要使用專案名稱做為 Visual C\# 類別檔 \(Class1.cs\) 中的命名空間名稱，請使用以下語法：  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 當您在專案範本的 .vstemplate 檔中參考 Class1.cs 檔時，請加入以下的 XML：  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## 請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)