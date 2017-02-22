---
title: "如何︰ 存取內建的字型和色彩配置 | Microsoft Docs"
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
  - "存取內建的字型"
  - "字型和色彩控制項 [Visual Studio SDK] 類別"
  - "存取內建的配置的色彩"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何︰ 存取內建的字型和色彩配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 整合式的開發環境 \(IDE\) 將其 \[編輯器\] 視窗相關聯字型和色彩的配置。 您可以存取透過此配置 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面。  
  
 若要使用的內建的字型和色彩配置，VSPackage 必須︰  
  
-   定義預設字型和色彩服務中使用的分類。  
  
-   預設字型和色彩伺服器中註冊的類別。  
  
-   建議您在 IDE 特定時段使用的內建的顯示項目和分類使用 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 和 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 介面。  
  
 IDE 會使用產生的類別目錄為視窗的控制代碼。 類別目錄的名稱會顯示在 **顯示設定︰** 下拉式清單方塊中的 **字型和色彩** 屬性頁。  
  
### 若要定義類別，使用內建的字型和色彩  
  
1.  建立任意的 GUID。  
  
     此 GUID 用來唯一識別類別**。**IDE 的預設字型和色彩的規格，此類別會重複使用。  
  
    > [!NOTE]
    >  字型和色彩以擷取資料時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 或其他介面，VSPackages 使用此 GUID，以參考內建的資訊。  
  
2.  類別目錄的名稱必須加入 VSPackage 的資源 \(.rc\) 檔，請在字串資料表，使它可以視需要在 IDE 中顯示當地語系化。  
  
     如需詳細資訊，請參閱[Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string)。  
  
### 若要註冊分類，使用內建的字型和色彩  
  
1.  建構一種特殊類型的類別目錄中的下列位置的登錄項目︰  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< Visual Studio 版本 \>*\\FontAndColors\\*\< 類別目錄 \>*\]  
  
     *\< 類別目錄 \>* 為非當地語系化的類別目錄名稱。  
  
2.  填入登錄，以使用內建的字型和色彩配置具有四個值︰  
  
    |名稱|類型|資料|描述|  
    |--------|--------|--------|--------|  
    |分類|REG\_SZ|GUID|任意的 GUID 識別的類別，其中包含內建的字型和色彩配置。|  
    |封裝|REG\_SZ|GUID|{} F5E7E71D\-1401\-11D1\-883B\-0000F87579D2<br /><br /> 這個 GUID 可供使用的預設字型和色彩設定的所有 Vspackage。|  
    |NameID|REG\_DWORD|ID|在 VSPackage 中可當地語系化的分類名稱的資源識別碼。|  
    |ToolWindowPackage|REG\_SZ|GUID|VSPackage 實作的 GUID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 介面。|  
  
3.  
  
### 若要起始使用系統提供的字型和色彩  
  
1.  建立的執行個體 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 介面視窗的實作和初始化的過程。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 方法，以取得執行個體 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 介面對應至目前 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 執行個體。  
  
3.  呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 兩次。  
  
    -   使用一次呼叫 `VSEDITPROPID_ViewGeneral_ColorCategory`做為引數。  
  
    -   使用一次呼叫 `VSEDITPROPID_ViewGeneral_FontCategory` 做為引數。  
  
     此設定，並公開為屬性\] 視窗的預設字型和色彩的服務。  
  
## 範例  
 下列範例會起始使用內建的字型和色彩。  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## 請參閱  
 [使用字型和色彩](../extensibility/using-fonts-and-colors.md)   
 [取得字型和色彩資訊文字顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)