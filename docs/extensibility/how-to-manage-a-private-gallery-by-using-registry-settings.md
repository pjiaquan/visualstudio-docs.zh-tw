---
title: "如何︰ 使用登錄設定管理私人組件庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX 私用組件庫管理"
  - "管理 VSIX 私用組件庫"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何︰ 使用登錄設定管理私人組件庫
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您是系統管理員或獨立 Shell 擴充功能的開發人員，您可以控制存取控制項、 範本和 Visual Studio 組件庫、 範例庫或私用組件庫中的工具。 若要使用或無法使用組件庫，建立描述已修改的登錄機碼和其值的.pkgdef 檔。  
  
## 管理私用組件庫  
 您可以建立.pkgdef 檔案，來控制多部電腦上的組件庫的存取。 這個檔案必須具有下列格式。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories` 索引鍵參考的組件庫啟用或停用。 Visual Studio 組件庫和範例圖庫會使用下列儲存機制的 Guid:  
  
-   Visual Studio 組件庫︰ 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   範例庫︰ AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 `Disabled` 是選擇性的值。 根據預設，會啟用組件庫。  
  
 `Priority` 值會決定文件庫列示在 \[選項\] 對話方塊中的順序。 Visual Studio 元件庫優先順序 10，範例庫優先順序 20。 私用組件庫啟動 100 的優先權。 如果數個組件庫中有相同的優先順序值，以其出現的順序取決於其當地語系化值 `DisplayName` 屬性。  
  
 `Protocol` 是必要的 Atom 或 SharePoint 文件庫的值。  
  
 可能是 `DisplayName`, ，或兩者 `DisplayNameResourceID` 和 `DisplayNamePackageGuid`, ，必須指定。 如果指定 all，然後在 `DisplayNameResourceID` 和 `DisplayNamePackageGuid` 組用。  
  
## 停用 Visual Studio Gallery 使用.pkgdef 檔  
 您可以停用.pkgdef 檔中的組件庫。 下列項目會停用 Visual Studio 組件庫︰  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 下列項目會停用範例庫︰  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## 請參閱  
 [私用組件庫](../extensibility/private-galleries.md)