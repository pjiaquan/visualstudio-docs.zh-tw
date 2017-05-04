---
title: "IManagedAddin 介面 | Microsoft Docs"
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
helpviewer_keywords: 
  - "IManagedAddin 介面"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# IManagedAddin 介面
  您可以實作 IManagedAddin 介面，以建立載入 Managed VSTO 增益集的元件。 2007 Microsoft Office system 中已新增這個介面。  
  
## 語法  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## 方法  
 下表列出 IManagedAddin 介面所定義的方法。  
  
|名稱|描述|  
|--------|--------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|當 Microsoft Office 應用程式載入 Managed VSTO 增益集時呼叫。|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|只在 Microsoft Office 應用程式卸載 Managed VSTO 增益集之前呼叫。|  
  
## 備註  
 自 2007 Microsoft Office system 開始，Microsoft Office 應用程式會使用 IManagedAddin 介面協助載入 Office VSTO 增益集。 您可以實作 IManagedAddin 介面，針對 Managed VSTO 增益集建立自己的 VSTO 增益集載入器和執行階段，而不使用 VSTO 增益集載入器 \(VSTOLoader.dll\) 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。 如需詳細資訊，請參閱[VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)。  
  
## Managed 增益集的載入方式  
 當應用程式啟動時，會執行下列步驟：  
  
1.  應用程式會在下列登錄機碼底下尋找項目，以探索 VSTO 增益集：  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<應用程式名稱\>*\\Addins\\  
  
     這個登錄機碼下的每個項目都是 VSTO 增益集的唯一識別碼。 通常這會是 VSTO 增益集組件的名稱。  
  
2.  應用程式會在每個 VSTO 增益集的項目底下尋找 `Manifest` 項目。  
  
     Managed VSTO 增益集可以將資訊清單的完整路徑儲存在 HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<應用程式名稱\>*\\Addins\\*\<增益集 ID\>* 下的 `Manifest` 項目中。 資訊清單是一種檔案 \(通常是 XML 檔案\)，可提供協助載入 VSTO 增益集的資訊。  
  
3.  如果應用程式找到 `Manifest` 項目，則會嘗試載入 Managed VSTO 增益集載入器元件。 應用程式會嘗試建立實作 IManagedAddin 介面的 COM 物件，來完成這項作業。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包含 VSTO 增益集載入器元件 \(VSTOLoader.dll\)，您也可以透過實作 IManagedAddin 介面來建立自己的元件。  
  
4.  應用程式會呼叫 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法，並傳入 `Manifest` 項目的值。  
  
5.  [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 方法會執行載入 VSTO 增益集所需的工作，例如設定要載入之 VSTO 增益集的應用程式定義域和安全性原則。  
  
 如需 Microsoft Office 應用程式用來探索及載入 Managed VSTO 增益集之登錄機碼的詳細資訊，請參閱 [VSTO 增益集的登錄項目](../vsto/registry-entries-for-vsto-add-ins.md)。  
  
## 實作 IManagedAddin 的指引  
 如果您實作 IManagedAddin，則必須使用下列 CLSID 註冊包含實作的 DLL：  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Microsoft Office 應用程式會使用這個 CLSID 建立實作 IManagedAddin 的 COM 物件。  
  
> [!CAUTION]  
>  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中的 VSTOLoader.dll 也會使用這個 CLSID。 因此，如果您使用 IManagedAddin 建立自己的 VSTO 增益集載入器和執行階段元件，則無法將元件部署到執行相依於 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 之 VSTO 增益集的電腦。  
  
## 請參閱  
 [Unmanaged API 參考 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  