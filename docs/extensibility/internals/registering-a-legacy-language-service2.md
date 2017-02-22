---
title: "註冊舊版語言服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "註冊語言服務"
  - "語言服務，登錄資訊"
  - "登錄中，語言服務"
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 註冊舊版語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列章節提供的登錄項目清單的各種語言中可用的服務選項 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 登錄項目下, 面 *VS Reg 根* 等於 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*X.Y*, ，其中 *X.Y* 是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本號碼。  
  
## 語言服務選項的登錄項目  
 *VS Reg 根*\\Languages\\Language Services\\*語言名稱* 索引鍵可以包含下列值。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|*\< GUID \>*|語言服務的 GUID。|  
|LangResID|REG\_DWORD|0x0\-0xffff|資源識別元 \(ResID\) 語言的當地語系化的文字名稱的字串。|  
|封裝|REG\_SZ|*\< GUID \>*|VSPackage 的 GUID。|  
|ShowCompletion|REG\_DWORD|0\-1|指定是否 **陳述式完成** 選項 **選項** \] 對話方塊中已啟用。|  
|ShowSmartIndent|REG\_DWORD|0\-1|指定是否可以選取 **智慧** 中的縮排 **選項** \] 對話方塊中已啟用。|  
|RequestStockColors|REG\_DWORD|0\-1|指定是否自訂或預設色彩用來關鍵字的色彩。|  
|ShowHotURLs|REG\_DWORD|0\-1|指定使用者是否可以按一下 Url。|  
|預設為非作用的 Url|REG\_DWORD|0\-1|指定的初始設定 **啟用按一下方式的 URL 巡覽** 選項 **選項** 對話方塊。|  
|DefaultToInsertSpaces|REG\_DWORD|0\-1|指定語言服務是否有 「 插入空格 」 做為其預設值\] 索引標籤選項。|  
|ShowDropdownBarOption|REG\_DWORD|0\-1|啟用或停用 **導覽列** 選項 **選項** \] 對話方塊中，以顯示或隱藏 **導覽列**。|  
|僅適用於單一程式碼視窗|REG\_DWORD|0\-1|啟用或停用 **新視窗** 中選擇 **視窗** 語言服務的功能表。|  
|EnableAdvancedMembersOption|REG\_DWORD|0\-1|啟用或停用 **選項** 的對話方塊設定 **隱藏進階成員**。|  
|支援 CF\_HTML|REG\_DWORD|0\-1|指定編輯器\] 中啟用複製和貼上 HTML 資料。|  
|EnableLineNumbersOption|REG\_DWORD|0\-1|指定是否 **行號** 選項 **選項** 啟用語言服務的對話方塊。|  
|HideAdvancedMembersByDefault|REG\_DWORD|0\-1|指定是否隱藏進階的成員，例如私用欄位，以完成清單中。|  
|ShowBraceCompletion|REG\_DWORD|0\-1|指定是否 **大括號完成** 選項 **選項** \] 對話方塊中已啟用。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## 偵錯工具的語言選項的登錄項目  
 *VS Reg 根*\\Languages\\Language Services\\*語言名稱*\\Debugger Languages\\*GUID*\\ 金鑰可包含下列值。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|文字|預設值可用於文件的語言名稱。 這個索引鍵的名稱會有對應的項目中的運算式評估工具的 GUID *\< VS Reg 根 \>*\\AD7Metrics\\Expression 評估工具。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## 編輯器工具選項的登錄項目  
 您可以加入 EditorToolsOptions 機碼下的登錄機碼的屬性頁和屬性節點。 這些索引鍵和其值會識別在屬性頁 **選項** 對話方塊 \(在 **工具** 功能表\)，用來設定語言服務。 在下列範例中， *頁面名稱* 屬性頁的名稱和 *節點名稱* 位於樹狀結構中節點的名稱 **選項** 對話方塊。 必須分別指定頁面項目和節點的項目。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|ResID|此選項頁面的當地語系化的顯示名稱。 名稱可以是常值文字或 \#`nnn`, ，其中 `nnn` 附屬 DLL 的指定 VSPackage 中的字串資源識別碼。|  
|封裝|REG\_SZ|*GUID*|實作這個選項頁面的 VSPackage 的 GUID。|  
|頁面|REG\_SZ|*GUID*|屬性頁的 GUID，以要求從 VSPackage 藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法。 如果此登錄項目不存在，登錄機碼將說明節點，而不是頁面。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## 檔案名稱副檔名選項的登錄項目  
 檔案副檔名的項目應該包含前置句號，例如 「.myext 」。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|*GUID*|此檔案名稱副檔名類型的預設語言服務的服務 GUID。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## 編輯器選項的登錄項目  
 *VS Reg 根*\\Editors 索引鍵可以包含下列值︰  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|""|未使用。您可以將您的名稱如文件。|  
|DefaultToolboxTab|REG\_SZ|""|編輯器在作用中時，讓預設 \[工具箱\] 索引標籤的名稱。|  
|DisplayName|REG\_SZ|ResID|中顯示名稱 **開啟** 對話方塊。 名稱為標準格式字串資源識別碼或名稱。|  
|ExcludeDefTextEditor|REG\_DWORD|0\-1|用於 **開啟** 功能表命令。 如果您不想列出可用的編輯器，為特定檔案類型清單中的預設文字編輯器，設定此值為 1。|  
|LinkedEditorGUID|REG\_SZ|*\< GUID \>*|使用任何語言服務，可以使用的字碼頁支援開啟檔案。 例如，當您開啟.txt 檔使用 **開啟** 命令時，使用原始程式碼編輯器與編碼不會提供選項。<br /><br /> 指定子機碼的名稱，GUID 是字碼頁編輯器 factory。這個特定的登錄項目中指定的連結的 GUID 是規則編輯器 factory。 這個項目的是，如果 IDE 不會使用預設的編輯器中開啟檔案，IDE 會嘗試使用清單中的下一個編輯器。 這個下一步的編輯器應該不是字碼頁編輯器 factory，因為這個編輯器 factory 基本上是相同的編輯器 factory 失敗。|  
|封裝|REG\_SZ|*\< GUID \>*|顯示名稱 ResID VSPackage GUID。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## 邏輯檢視選項的登錄項目  
 *VS Reg 根*\\Editors\\*編輯器 GUI \>*\\LogicalViews 索引鍵可以包含下列值。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ||未使用。|  
|*\< GUID \>*|REG\_SZ|""|若要支援的邏輯檢視表的索引鍵。 您可以為多個所需。 登錄項目名稱是什麼是重要的是，不是值，都是空字串。|  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## 登錄項目編輯器延伸模組選項  
 *VS Reg 根*\\Editors\\*編輯器 GUID*\\Extensions 索引鍵可以包含下列值。 檔案的副檔名不包含前置句號。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ||未使用。|  
|*\< \> ext*|REG\_DWORD|0 0xffffffff|擴充功能的相對優先權。 如果兩個或多個語言都共用相同的副檔名，則會選擇較高優先順序的語言。|  
  
 此外，目前使用者的預設選項，編輯器會儲存在 HKEY\_Current\_User\\Software\\Microsoft\\VisualStudio\\*X.Y*\\Default Editors\\*ext*。 選取的語言服務的 GUID 是在自訂項目。 這個選項的目前使用者的優先順序。  
  
### 範例  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## 受管理的封裝架構語言服務選項的登錄項目  
 下列的登錄項目是針對受管理的封裝架構 \(MPF\) 語言服務類別。 這些登錄項目表示針對各種 IntelliSense 功能和其他進階編輯功能之語言服務中的支援。  
  
 這些登錄項目透過存取 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別。  
  
|名稱|類型|範圍|描述|  
|--------|--------|--------|--------|  
|CodeSense|REG\_DWORD|0\-1|IntelliSense 作業的支援。|  
|MatchBraces|REG\_DWORD|0\-1|比對的語言組大括號、 括號和括號等的支援。|  
|QuickInfo|REG\_DWORD|0\-1|IntelliSense 快速諮詢作業的支援。|  
|ShowMatchingBrace|REG\_DWORD|0\-1|在狀態列中顯示成對的語言支援。|  
|MatchBracesAtCaret|REG\_DWORD|0\-1|顯示語言配對，通常是透過反白顯示的兩個元素的支援。|  
|MaxErrorMessages|REG\_DWORD|0\-n|中可能顯示的錯誤數目上限 **錯誤清單** 視窗。|  
|CodeSenseDelay|REG\_DWORD|0\-n|要初始化任何背景剖析 IntelliSense 作業之前的延遲時間的毫秒數。|  
|EnableAsyncCompletion|REG\_DWORD|0\-1|背景剖析支援。|  
|EnableCommenting|REG\_DWORD|0\-1|支援標記為註解選取的文字區塊，也可能指定支援取消註解所選取的文字。|  
|EnableFormatSelection|REG\_DWORD|0\-1|支援格式化文字，例如自動縮排或調整的括號位置。|  
|AutoOutlining|REG\_DWORD|0\-1|大綱 （可摺疊的區域） 的支援。|  
|MaxRegions|REG\_DWORD|0\-n|每個檔案的隱藏區域的數目上限。|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## 請參閱  
 [開發語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)