---
title: "如何：不成功的 Visual Studio 專案升級疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "升級應用程式, Visual Studio"
  - "升級專案 [Visual Studio]"
  - "專案 [Visual Studio], 升級"
  - "Visual Studio 轉換精靈"
  - "轉換精靈"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 如何：不成功的 Visual Studio 專案升級疑難排解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有時候 Visual Studio 無法完全轉換從舊版 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來的專案。  如果下一節的提示不解決您的問題，您可以找到有關 TechNet [Wiki:開發入口網站](http://go.microsoft.com/fwlink/?LinkId=254808)的詳細資訊。  
  
## 因為找不到檔案導致無法執行專案  
 專案檔包含經過硬式編碼的檔案路徑，當您按 F5 時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會使用這些路徑來執行專案。  這些路徑可能包含 devenv.exe 和其他必要檔案的位置。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已升級的版本，其可能變更這些檔案的路徑。  
  
#### 若要解決不正確的檔案路徑  
  
1.  使用文字編輯器開啟您的專案檔。  
  
2.  掃描可能不正確的檔案路徑，特別是包含 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本號碼的檔案路徑。  
  
3.  修改不正確的檔案路徑，讓這些路徑都指向新的目標。  
  
## 因為參考無效導致無法建置專案  
 當您升級 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]時，您可能也會升級 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  如果新版 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 不再支援您專案包含的參考，解析這些參考時可能就會有不正確的情形發生。  特別是包含版本號碼的參考最可能發生這種情形，例如 `Microsoft.VisualStudio.Shell.Interop.8.0`。  
  
 如果您的程式碼包含許多無效參考，最簡單的解決方式就是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的多目標功能，以舊版 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 為目標。  
  
#### 若要解決不正確的檔案參考  
  
1.  使用文字編輯器開啟您的專案檔。  
  
2.  開啟專案屬性。  
  
3.  選取正確的 \[**目標 Framework**\] 值。  或者，您可以直接在專案檔中修改 `<TargetFrameworkVersion>` 項目的值。  
  
 如果您希望自己的專案在已升級的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本中執行，就必須更新專案的參考，並且更新呼叫這些參考的所有 `Imports` 或 `Using` 陳述式。  如果您的專案在 IDE 載入，您可以使用 \[**方案總管**\] 或 \[**參考管理員**\] 對話方塊更新參考。  
  
## 請參閱  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)