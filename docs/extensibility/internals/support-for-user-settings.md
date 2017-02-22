---
title: "使用者設定的支援 | Microsoft Docs"
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
  - "自訂設定的點"
  - "使用者設定 [Visual Studio SDK]，註冊持續性支援"
  - "持續性、 登錄設定"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用者設定的支援
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 可能會定義一或多個設定分類，也就是保存在使用者選擇時的狀態變數群組 **匯入\/匯出設定** 命令 **工具** 功能表。 若要啟用此持續性，您可以使用的設定 Api 中 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 登錄項目，稱為自訂設定點和 GUID 定義類別的 VSPackage 設定。 VSPackage 可以支援多個設定分類，每個定義的自訂設定的點。  
  
-   設定 interop 組件為基礎的實作 \(使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 介面\) 應該編輯登錄，或使用登錄器指令碼 （.rgs 檔） 建立自訂設定的點。 如需詳細資訊，請參閱[Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)。  
  
-   使用管理套件架構 \(MPF\) 的程式碼應該建立自訂設定的點，藉由附加 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 到 VSPackage 的自訂設定的每個點。  
  
     如果單一 VSPackage 支援數個自訂設定的點，每個自訂設定的點由個別的類別，實作每個已註冊的唯一執行個體的 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 類別。 因此，實作類別的設定可以支援多個類別的設定。  
  
## 自訂設定點登錄項目詳細資料  
 在下列位置的登錄項目建立自訂設定點︰ HKLM\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\UserSettings\\`<CSPName>`, ，其中 `<CSPName>` VSPackage 支援是自訂設定端點的名稱和 *\< 版本 \>* 的版本 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，例如 8.0。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 的根路徑*\< 版本 \>* 可以覆寫以替代根時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式的開發環境 \(IDE\) 會初始化。 如需詳細資訊，請參閱[命令列參數](../../extensibility/command-line-switches-visual-studio-sdk.md)。  
  
 登錄項目的結構如下所示︰  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< 版本 \>*\\UserSettings\\  
  
 `<CSPName`\> \= '\#12345' s  
  
 封裝 \= ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 類別 \= ' {釋出 YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 ResourcePackage \= ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent \= 類別名稱  
  
|名稱|類型|資料|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|自訂設定點的名稱|索引鍵的名稱， `<CSPName`\>，為自訂設定點的未當地語系化的名稱。<br /><br /> 根據 MPF 實作，藉由合併取得的索引鍵名稱 `categoryName` 和 `objectName` 引數的 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 建構函式到 `categoryName_objectName`。<br /><br /> 索引鍵可以是空的或它可以包含在附屬 DLL 中的當地語系化字串的參考識別碼。 這個值取自 `objectNameResourceID` 引數 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 建構函式。|  
|封裝|REG\_SZ|GUID|VSPackage 可實作自訂設定點的 GUID。<br /><br /> 實作根據 MPF 使用 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 類別，請使用建構函式的 `objectType` 引數包含 VSPackage <xref:System.Type> 和反映來取得這個值。|  
|分類|REG\_SZ|GUID|識別 \[設定\] 類別的 GUID。<br /><br /> Interop 組件為基礎的實作，這個值可以是任意選擇的 GUID，其 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會將傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法。 這兩種方法的所有實作應該先都確認其 GUID 引數。<br /><br /> 如需根據 MPF 實作，此 GUID 藉由取得 <xref:System.Type> 類別實作的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定機制。|  
|ResourcePackage|REG\_SZ|GUID|選擇項。<br /><br /> 如果實作 VSPackage 未提供這些附屬 DLL 包含路徑的當地語系化字串。<br /><br /> MPF 會使用反映來取得正確的資源 VSPackage，所以 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 類別並不會設定這個引數。|  
|AlternateParent|REG\_SZ|在 \[工具選項\] 頁面包含此自訂設定點資料夾的名稱。|選擇項。<br /><br /> 您必須將此值，只有支援的設定實作 **工具選項** 使用持續性機制中的頁面 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 而不是在儲存狀態的自動化模型的機制。<br /><br /> 在這些情況下，AlternateParent 機碼中的值是 `topic` 區段 `topic.sub-topic` 用來識別特定字串 **工具選項** 頁面。 例如，對於 **工具選項** 頁面 `"TextEditor.Basic"` AlternateParent 的值會是 `"TextEditor"`。<br /><br /> 當 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 會產生自訂設定的點，它會是做為類別名稱相同。|