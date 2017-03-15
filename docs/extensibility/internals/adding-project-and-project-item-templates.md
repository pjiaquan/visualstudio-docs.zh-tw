---
title: "加入專案和專案項目範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK] 加入"
  - "專案項目 [Visual Studio] 加入"
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 加入專案和專案項目範本
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您建立自己的專案型別時，您必須提供支援加入新的專案和專案項目使用標準的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合開發環境 \(IDE\) 的對話方塊。  下列主題將討論不同的技術，來加入專案和專案項目。  
  
## 在本節中  
 [專案內容](../../extensibility/internals/project-context.md)  
 說明專案提供的大部分簡化環境中的內容資訊。  
  
 [專案的優先順序](../../extensibility/internals/project-priority.md)  
 說明專案項目通常是一個專案的成員，以協助避免模稜兩可，了解哪種專案用來開啟項目。  
  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)  
 提供專案在決定要使用開啟的專案項目時所扮演的兩種編輯器，可用以開啟 \[專案\] 和 \[角色\] 中的 \[檔案類型的資訊。  
  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)  
 說明的動作時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在建立專案。  
  
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 說明的程序加入項目至**加入新項目**對話方塊。  
  
 [將目錄加入至新的 \[專案\] 對話方塊](../Topic/Adding%20Directories%20to%20the%20New%20Project%20Dialog%20Box.md)  
 提供註冊新的目錄包含 VSPackage 所提供的自訂範本的範例。  
  
 [新增目錄來加入新項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 提供範例，註冊一組新的目錄的**加入新項目**對話方塊。  
  
 [IDE 定義的命令，來擴充專案系統](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 列出不同類型的指令擴充專案系統所使用的項目。  
  
 [物件，通常會用來擴充專案的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 列出用來擴充的物件的 catid 的方式[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]，以及[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案系統。  
  
## 相關章節  
 [如何: 開啟專案的特定編輯器](../../extensibility/how-to-open-project-specific-editors.md)  
 提供逐步的指示，來開啟本質上繫結至特定編輯器中為專案項目。  
  
 [如何: 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)  
 提供開啟標準編輯器的逐步指示。  
  
 [專案子類型](../../extensibility/internals/project-subtypes.md)  
 提供專案子類型觀念性主題的連結。  專案子類型擴充現有的[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供其他主題的連結，提供有關如何設計新的專案類型的資訊。