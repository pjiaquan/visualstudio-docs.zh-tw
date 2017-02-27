---
title: "註冊專案和項目範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，加入項目"
  - "登錄中，加入新項目] 對話方塊"
  - "加入新項目對話方塊"
  - "加入新專案對話方塊"
  - "登錄中，加入新的專案對話方塊"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 註冊專案和項目範本
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案類型必須登錄其專案和專案項目範本的所在位置的目錄。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用您的專案型別相關聯的登錄資訊來決定要顯示在 **加入新的專案** 和 **加入新項目** 對話方塊。  
  
 如需範本的詳細資訊，請參閱 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
## 專案的登錄項目  
 下列範例會顯示在 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ 下的登錄項目 \<*版本*\>。 伴隨表格說明的範例中使用的項目。  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|名稱|類型|描述|  
|--------|--------|--------|  
|@|REG\_SZ|這類專案的預設名稱。|  
|DisplayName|REG\_SZ|附屬 DLL 從擷取的資源識別碼的名稱登錄封裝底下。|  
|封裝|REG\_SZ|登錄封裝底下之封裝的類別 ID。|  
|ProjectTemplatesDir|REG\_SZ|預設的專案範本檔案的路徑。 專案範本檔案會顯示 **新的專案** 範本。|  
  
### 登錄項目範本  
 您必須註冊儲存項目範本的目錄。  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|名稱|類型|描述|  
|--------|--------|--------|  
|@|REG\_SZ|加入項目範本的資源識別碼。|  
|TemplatesDir|REG\_SZ|在對話方塊中顯示的專案項目路徑 **加入新項目** 精靈。|  
|TemplatesLocalizedSubDir|REG\_SZ|TemplatesDir 的子目錄名稱的字串資源識別碼會保留當地語系化的範本。 因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 載入字串資源的附屬 Dll 如果有的話，每個附屬 DLL 可以包含不同的當地語系化的子目錄名稱。|  
|SortPriority|REG\_DWORD|設定來管理範本中的顯示的順序 SortPriority **加入新項目** 對話方塊。 較大的 SortPriority 值稍早出現在 \[範本\] 清單。|  
  
### 註冊檔案篩選器  
 （選擇性） 您可以註冊的篩選器， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時它會提示輸入檔案名稱使用。 例如， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 篩選 **開啟檔案** 對話方塊︰  
  
 **Visual C\# 檔案 （\*.cs、 \*.resx、 \*.settings、 \*.xsd、 \*.wsdl），則為.cs，\*.resx、 \*.settings、 \*.xsd、 \*.wsdl\)**  
  
 若要支援註冊多個篩選器，每個篩選條件註冊在它自己的子機碼下 HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*版本*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*子機碼*\>。 子機碼名稱是任意的。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 子機碼的名稱時，使用只是它的值。  
  
 您可以控制藉由設定旗標下, 表顯示使用的篩選的內容。 如果篩選器沒有設定任何旗標，它將會列出中常見的篩選條件之後 **加入現有項目** 對話方塊和 **開啟檔案** 對話方塊中，但它不會使用在 **檔案中尋找** 對話方塊。  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|名稱|類型|描述|  
|--------|--------|--------|  
|CommonFindFilesFilter|REG\_DWORD|可在其中一個常見的篩選器的篩選 **檔案中尋找** 對話方塊。 一般篩選器會列在之前未標示為通用篩選器的篩選器清單。|  
|CommonOpenFilesFilter|REG\_DWORD|可在其中一個常見的篩選器的篩選 **開啟檔案** 對話方塊。 一般篩選器會列在之前未標示為通用篩選器的篩選器清單。|  
|FindInFilesFilter|REG\_DWORD|列出的篩選中的一般篩選器之後 **檔案中尋找** 對話方塊。|  
|NotOpenFileFilter|REG\_DWORD|表示在不使用篩選器 **開啟檔案** 對話方塊。|  
|NotAddExistingItemFilter|REG\_DWORD|表示在不使用篩選器 **加入現有項目** 對話方塊。|  
|SortPriority|REG\_DWORD|設定 SortPriority 來管理篩選器所顯示的順序。 較大的 SortPriority 值稍早出現在篩選器清單。|  
  
## 目錄結構  
 VSPackages 可以將範本檔案和資料夾任何地方在本機或遠端磁碟上，只要透過整合式的開發環境 \(IDE\) 註冊的位置。 不過，為了方便組織，我們建議產品的安裝路徑下的下列目錄結構。  
  
 \\Templates  
  
 \\Projects （包含專案範本）  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems （包含專案項目）  
  
 \\Class  
  
 \\Form  
  
 \\Web 頁面  
  
 \\HelperFiles （包含多個檔案的專案項目中使用的檔案）  
  
 \\WizardFiles  
  
## 請參閱  
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [當地語系化應用程式](../../ide/localizing-applications.md)   
 [物件，通常會用來擴充專案的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)