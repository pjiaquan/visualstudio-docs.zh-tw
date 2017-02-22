---
title: "何時建立專案類型 | Microsoft Docs"
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
  - "專案類型，建立的條件"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 何時建立專案類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立新的專案類型提供一個自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]為您的使用者。  不過，建立新的專案類型並不需要所有[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自訂項目。  下列方針應該可以幫助您判斷新的專案型別是否需要針對您的案例。  
  
## 建立新的專案類型  
 您必須先建立專案型別，如果您想要自訂[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]內一或多個下列方式：  
  
-   參與建置、 部署組態和原始檔控制。  
  
-   提供偵錯支援。  
  
-   顯示專案中的項目**方案總管\] 中**。  
  
-   使用**開啟的專案** 或 **新的專案**對話方塊。  
  
-   專案支援巢狀結構。  
  
## 擴充現有的專案型別  
 您可能想要建立新的專案類型，可以用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下列方式來修改或擴充現有的專案類型的行為，例如，修改的建置處理序[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案：  
  
-   使用多個檔案視為單一單位。  
  
-   單一檔案顯示的子項目階層架構。  
  
-   顯示命令內容周圍編輯器。  
  
-   編輯器會顯示在服務方面。  
  
## 使用現有的專案類型  
 建立新的專案不有時需要。  下表是您沒有建立的專案類型的工作。  
  
|工作|描述|  
|--------|--------|  
|處理命令|任何 VSPackage 可以處理命令。|  
|建置編輯器|註冊自訂編輯器。  如需詳細資訊，請參閱 [Document Windows and Editors](http://msdn.microsoft.com/zh-tw/603625e1-62b6-413a-bc44-089346e166bc)。|  
|主控視窗|您可以建立 \[工具\] 和 \[文件視窗而不加入新的專案類型。|  
|公開屬性\] 視窗中的屬性|所有的物件可以公開 \(expose\) 屬性。|  
  
## 建立專案的子型別  
 您可以使用專案的子型別來擴充受管理的專案類型，而不必建立新的專案類型。  專案子類型以延伸 Microsoft 所撰寫的 managed 的專案中使用 COM 彙總[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]。  具有 COM 彙總，您可以重複使用 managed 的專案系統實作，並仍透過彙總，並使用支援介面的特定案例進行自訂。  如需有關專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## 請參閱  
 [Document Windows and Editors](http://msdn.microsoft.com/zh-tw/603625e1-62b6-413a-bc44-089346e166bc)   
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)