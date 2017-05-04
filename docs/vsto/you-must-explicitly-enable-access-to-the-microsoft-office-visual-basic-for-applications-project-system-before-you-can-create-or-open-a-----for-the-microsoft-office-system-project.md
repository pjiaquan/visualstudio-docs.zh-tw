---
title: "您必須明確啟用存取 Microsoft Office Visual Basic for Applications 專案系統，然後才能建立或開啟 Visual Studio Tools for the Microsoft Office System 專案 | Microsoft Docs"
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
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 您必須明確啟用存取 Microsoft Office Visual Basic for Applications 專案系統，然後才能建立或開啟 Visual Studio Tools for the Microsoft Office System 專案
  Office 開發專案需要存取 Microsoft Office Word 和 Microsoft Office Excel 中的 Visual Basic for Applications 專案系統，即使專案並未使用 Visual Basic for Applications 亦然。  執行階段所支援 Visual Basic 和 C\# 專案的控制項，取決於 Visual Basic for Applications 專案系統。  
  
 某些 Microsoft Office 巨集病毒會嘗試自動執行 Visual Basic for Applications 專案系統，以傳播自己本身。  當您啟用對 Visual Basic for Applications 專案系統的存取時，您將會移除協助防止巨集病毒散播的保護機制。  不過仍會保留一般的巨集安全性，因此會使用您為 Office 應用程式所維護的巨集安全性層級和受信任發行者清單來判斷是否可以在電腦上執行巨集。  
  
> [!NOTE]  
>  這僅適用於開發電腦。  使用者電腦不需要啟用此選項即可執行 Office 方案。  
  
 請務必注意，只是停用對 Visual Basic for Applications 專案系統的存取並不會保護您不受病毒的攻擊，這樣做只會在您的電腦真的遭到巨集病毒的危害時，停止將某些病毒散播到其他文件。  此選項預設為停用狀態，以便為電腦增加一個保護層，但是如果您依照下列安全性最佳做法進行再啟用此選項，您的電腦就比較不容易遭到病毒的危害。  
  
 針對 Office 巨集病毒的最佳保護做法是在「高」或「非常高」的安全性層級上執行 Office、只信任經驗證且已知來源的巨集，以及安裝最新版的安全性修補程式和病毒掃描程式。  
  
 如需保護電腦不受病毒及其他可疑程式碼危害的詳細資訊，請參閱 [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect)。  
  
 您可以手動啟用或停用 \[信任存取 Visual Basic 專案\]。  
  
 如果出現 VBA 或 COM 錯誤，您可以修復 Office 的安裝。  
  
### 啟用或停用 Visual Basic 專案的存取  
  
1.  在 Word 或 Excel 的 \[工具\] 功能表上，指向 \[巨集\]，然後按一下 \[安全性\]。  
  
2.  在 \[安全性\] 對話方塊中，按一下 \[受信任的發行者\] 索引標籤。  
  
3.  選取 \[信任存取 Visual Basic 專案\] 加以啟用，或清除選項加以停用。  
  
4.  按一下 \[**確定**\]。  
  
### 設定 Office 巨集安全性層級  
  
1.  在 Word 或 Excel 的 \[工具\] 功能表上，指向 \[巨集\]，然後按一下 \[安全性\]。  
  
2.  在 \[安全性層級\] 索引標籤上，選取所需的設定。  
  
     \[安全性層級\] 索引標籤內含各個層級的詳細資料。  如需詳細資訊，請參閱 Office 說明中的＜巨集安全性層級＞。  
  
### 安裝 2007 Microsoft Office 系統的 VBA  
  
1.  在控制台中執行 \[新增或移除程式\] 或 \[程式和功能\]。  
  
2.  在 \[目前安裝的程式\] 清單中選取 \[Office\]。  
  
3.  按一下 \[變更\]。  
  
4.  選取 \[新增或移除功能\]，然後按一下 \[繼續\]。  
  
5.  選取 \[選擇應用程式的進階自訂\]，然後按 \[下一步\]。  
  
6.  展開 \[選擇應用程式和工具的更新選項\] 清單中的 \[Office 共用的功能\]。  
  
7.  開啟 \[Visual Basic for Applications\] 旁的下拉式功能表，然後按一下 \[從我的電腦執行\]。  
  
8.  按一下 \[**繼續**\]。  
  
9. 按一下 \[**關閉**\]。  
  
### 修復 Office 的安裝  
  
1.  在控制台中執行 \[新增或移除程式\] 或 \[程式和功能\]。  
  
2.  在 \[目前安裝的程式\] 清單中選取您的 Office 版本。  
  
3.  按一下 \[變更\]。  
  
4.  選取 \[重新安裝或修復\]，然後按 \[下一步\]。  
  
5.  選取 \[偵測並修復 Office 中的安裝錯誤\]，然後按一下 \[安裝\]。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)  
  
  