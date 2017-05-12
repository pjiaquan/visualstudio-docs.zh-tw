---
title: "讓表單區域與 Outlook 訊息類別產生關聯"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "表單區域 [Visual Studio 中的 Office 程式開發], 訊息類別"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 讓表單區域與 Outlook 訊息類別產生關聯
  您可以將表單區域關聯至每個項目的訊息類別，以指定要顯示表單區域的 Microsoft Office Outlook 項目。  例如，如果您想要將表單區域附加至郵件項目底部，則可以將表單區域關聯至 IPM.Note 訊息類別。  
  
 若要將表單區域關聯至訊息類別，請在 \[**新的 Outlook 表單區域**\] 精靈中指定訊息類別名稱，或是將屬性套用至表單區域 Factory 類別。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 了解 Outlook 訊息類別  
 Outlook 訊息類別會識別 Outlook 項目類型。  下表列出八個標準項目類型與其訊息類別名稱。  
  
|Outlook 項目類型|訊息類別名稱|  
|------------------|------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post 或 IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 您也可以指定自訂訊息類別的名稱。  自訂訊息類別會識別您於 Outlook 中定義的自訂表單。  
  
> [!NOTE]  
>  您可以針對取代型和全部取代型表單區域指定新的自訂訊息類別名稱。  不必使用現有自訂表單的訊息類別名稱。  自訂訊息類別的名稱必須是唯一的。  確保唯一名稱的一種方式，就是使用如下的命名慣例：\<*StandardMessageClassName*\>.\<*Company*\>.\<*MessageClassName*\> \(例如：IPM.Note.Contoso.MyMessageClass\)。  
  
## 讓表單區域與 Outlook 訊息類別產生關聯  
 有兩種方式可以將表單區域關聯至訊息類別：  
  
-   使用 \[**新的 Outlook 表單區域**\] 精靈。  
  
-   套用類別屬性。  
  
### 使用新的 Outlook 表單區域精靈  
 您可以在 \[**新的 Outlook 表單區域**\] 精靈的最後一頁選取標準訊息類別，並針對您要與表單區域產生關聯的自訂訊息類別輸入其名稱。  
  
 如果表單區域是用來取代整個表單或是表單的預設頁面，則您將無法使用標準訊息類別。  您只能針對可將新頁面加入至表單的表單，或是附加至表單底部的表單，指定標準訊息類別名稱。  如需詳細資訊，請參閱[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 若要包含一個或多個自訂訊息類別，請將其名稱輸入至 \[**將顯示此表單區域的自訂訊息類別為何?**\] 方塊。  
  
 您輸入的名稱必須符合下列方針：  
  
-   使用完整的訊息類別名稱 \(例如："IPM.Note.Contoso"\)。  
  
-   用分號來分隔多個訊息類別名稱。  
  
-   請勿加入標準 Outlook 訊息類別，例如 "IPM.Note" 或 "IPM.Contact"。  請只加入自訂訊息類別，例如 "IPM.Note.Contoso"。  
  
-   請勿僅指定基底訊息類別 \(例如："IPM"\)。  
  
-   每個訊息類別名稱不得超過 256 個字元。  
  
 \[**新的 Outlook 表單區域**\] 精靈會在您按一下 \[**完成**\] 時，驗證輸入格式。  
  
> [!NOTE]  
>  \[**新的 Outlook 表單區域**\] 精靈無法驗證您提供的訊息類別名稱是否正確或有效。  
  
 在您完成精靈之後，\[**新的 Outlook 表單區域**\] 精靈會將屬性套用至包含指定之訊息類別名稱的表單區域類別。  您也可以手動套用這些屬性。  
  
### 套用類別屬性  
 在您完成 \[**新的 Outlook 表單區域**\] 精靈後，可以將表單區域關聯至 Outlook 訊息類別。  若要這麼做，請將這些屬性套用至表單區域 Factory 類別。  
  
 下列範例示範兩個已套用至 `myFormRegion` 表單區域 Factory 類別的 <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> 屬性。  第一個屬性會將表單區域關聯至郵件表單的標準訊息類別。  第二個屬性則會將表單區域關聯至名為 `IPM.Task.Contoso` 的自訂訊息類別。  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 屬性必須符合下列方針：  
  
-   請針對自訂訊息類別使用完整的訊息類別名稱 \(例如："IPM.Note.Contoso"\)。  
  
-   請勿僅指定基底訊息類別 \(例如："IPM"\)。  
  
-   每個訊息類別名稱不得超過 256 個字元。  
  
-   如果表單區域將取代整個表單或是表單的預設頁面，則請勿加入標準訊息類別的名稱。  您只能針對可將新頁面加入至表單的表單，或是附加至表單底部的表單，指定標準訊息類別名稱。  如需詳細資訊，請參閱[如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)。  
  
 Visual Studio 會在您建置專案時，驗證訊息類別名稱的格式。  
  
> [!NOTE]  
>  Visual Studio 無法驗證您提供的訊息類別名稱是否正確或有效。  
  
## 請參閱  
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [建立 Outlook 表單區域的方針](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [如需表單名稱和訊息類別。](HV01044315)   
 [Outlook 如何形成，而項目](HV01044298)  
  
  