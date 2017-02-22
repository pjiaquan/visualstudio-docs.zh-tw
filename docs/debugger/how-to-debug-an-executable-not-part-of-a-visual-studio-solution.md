---
title: "如何：偵錯不屬於 Visual Studio 方案的可執行檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 可執行檔"
  - "可執行檔, 專案外偵錯"
  - "可執行檔, 匯入"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：偵錯不屬於 Visual Studio 方案的可執行檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有時，您可能想要偵錯非 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中的可執行檔。  這種可執行檔可能是您在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之外所建立的可執行檔，或是您從別處取得的可執行檔。  
  
 這個問題的一般解決方法是，從 Visual Studio 外啟動該可執行檔，並使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯工具附加於其上。  如需詳細資訊，請參閱[附加至執行中處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 附加至一個應用程式需要某些手動步驟，因此需要花上幾秒鐘。  這種略微延遲表示出，附加偵錯工具對嘗試偵錯一個啟動時所發生的問題無益。  此外，如果您正在偵錯一個不會等候使用者輸入且會很快就結束的程式，您可能沒有時間在該程式附加偵錯工具。  如果您已安裝 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]，您可以建立這種程式的 EXE 專案。  
  
### 若要為現有的可執行檔建立 EXE 專案  
  
1.  在 \[**檔案**\] 功能表上按一下 \[**開啟**\]，並選擇 \[**專案**\]。  
  
2.  在 \[**開啟專案**\] 對話方塊中，按一下 \[**檔案名稱**\] 方塊旁邊的下拉式清單，然後選取 \[**所有專案檔**\]。  
  
3.  找出該可執行檔，然後按一下 \[**確定**\]。  
  
     這樣便可以建立包含該可執行檔的暫時方案。  
  
### 若要將可執行檔匯入至 Visual Studio 方案中  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**所有專案**\]，再按一下 \[**現有專案**\]。  
  
2.  在 \[**加入現有專案**\] 對話方塊中，按一下 \[**檔案名稱**\] 方塊旁邊的下拉式清單，然後選取 \[**所有專案檔**\]。  
  
3.  找出並選取可執行檔。  
  
4.  按一下 \[**確定**\]。  
  
5.  從 \[**偵錯**\] 功能表選擇一個執行命令 \(例如 \[**啟動**\]\) 啟動該可執行檔。  
  
    > [!NOTE]
    >  並非所有的程式語言都支援 EXE 專案。  如果您需要使用這項功能，請安裝 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]。  
  
     當您在偵錯沒有原始程式碼的可執行檔時，不論您是附加到正在執行的可執行檔，或者是將可執行檔加入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案，可用的偵錯功能都會受到限制。  如果可執行檔在建置時沒有相容格式的偵錯資訊，將更進一步地限制可用功能。  如果您有原始程式碼，最好的方法是將原始程式碼匯入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中建立偵錯版的可執行檔。  
  
## 請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/zh-tw/91e449e9-8b65-4123-960f-2107cd1f1cfd)