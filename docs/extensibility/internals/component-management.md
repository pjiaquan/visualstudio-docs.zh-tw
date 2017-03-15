---
title: "管理元件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安裝 [Visual Studio SDK] 元件"
  - "安裝 [Visual Studio SDK]，檔案管理"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 管理元件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Windows 「 安裝程式中的工作單位稱為 \(有時稱為 WICs 或只是元件\) 的 Windows 安裝程式元件。  GUID 會識別每個 WIC，也就是 「 基本單位安裝與參考計數若是使用 Windows 安裝程式的設定。  
  
 雖然您可以使用數個產品建立您的 VSPackage 安裝程式時，以下的討論假設使用的 Windows 安裝程式 \(.msi\) 檔案。  在建立您的安裝程式時，您必須正確地管理檔案部署，以便正確的參考計數會發生在任何時間。  因此，不同版本的產品將不會干擾或破壞彼此中安裝多種和解除安裝案例。  
  
 在 \[Windows 安裝程式，參考計數發生於元件層級。  您必須小心地整理您的資源 ； 檔案、 登錄項目等等 — 成元件。  有其他層級的組織 — 例如模組、 功能和產品，可協助在不同狀況下。  如需詳細資訊，請參閱 [Windows 安裝程式的基本概念](../../extensibility/internals/windows-installer-basics.md)。  
  
## 撰寫並排顯示安裝的安裝程式的指導方針  
  
-   作者的檔案和登錄機碼成他們自己的元件版本之間共用的。  
  
     這可讓您輕鬆地使用它們在下一個版本。  比方說，全域註冊的型別程式庫檔案的副檔名，註冊 HKEY\_CLASSES\_ROOT，而其他項目。  
  
-   群組到上一單獨合併模組的共用的元件。  
  
     這可協助作者正確設定並存向前移動。  
  
-   使用相同的 Windows 安裝程式元件版本之間，即可安裝共用的檔案及登錄機碼。  
  
     如果您使用不同的元件時，檔案和登錄項目都解除安裝時解除安裝某個版本的 VSPackage，但仍安裝其他的 VSPackage。  
  
-   不要混合建立版本編號以及共用相同的元件中的項目。  
  
     如此一來，因此無法安裝共用的項目通用的位置，並已建立版本的項目到隔離的位置。  
  
-   沒有建立版本的檔案的共用的登錄機碼。  
  
     如果您這麼做，另一個版本的 VSPackage 安裝時將會覆寫共用的金鑰。  移除第二個版本之後，檔案的索引鍵會指出指標是看不見了。  
  
## 請參閱  
 [選擇 \[共用和版本建立 Vspackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)