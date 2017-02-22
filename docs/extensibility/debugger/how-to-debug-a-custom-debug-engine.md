---
title: "How To: 偵錯自訂的偵錯引擎 | Microsoft Docs"
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
  - "偵錯引擎，偵錯"
  - "偵錯 [偵錯 SDK]，自訂的偵錯引擎"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# How To: 偵錯自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案類型中啟動偵錯引擎 \(DE\) <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法。  這表示 DE 就會啟動所控制的執行個體的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]控制的專案類型。  不過，該執行個體的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無法偵錯 DE。  下面這樣是為了讓您偵錯您的自訂 DE 步驟。  
  
> [!NOTE]
>  ： 在 「 偵錯自訂偵錯引擎 」 程序中，您必須等待開始之前，您可以附加至這個 DE。  如果您將一個訊息方塊 DE 啟動時，就會出現您 DE 開端附近時，您可以附加在該點，然後再清除 \[訊息方塊，才能繼續。  如此一來，您可以攔截所有 DE 事件。  
  
> [!WARNING]
>  您必須擁有您嘗試使用下列程序之前，安裝遠端偵錯。  如需詳細資訊，請參閱[遠端偵錯](../../debugger/remote-debugging.md)。  
  
### 偵錯自訂偵錯引擎  
  
1.  啟動 msvsmon.exe，遠端偵錯監視器。  
  
2.  從**工具** \] 功能表中選取 msvsmon.exe **選項** 開啟 **選項**對話方塊。  
  
3.  選取 「 不驗證 」 選項，然後按一下 \[ **確定**。  
  
4.  啟動執行個體的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並開啟自訂 DE 專案。  
  
5.  啟動第二個執行個體的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，然後開啟您自訂的專案啟動 DE \(進行開發，通常是在實驗性質的登錄 hive 設定安裝 VSIP 時\)。  
  
6.  這個第二個執行個體中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 從您的自訂專案載入原始程式檔，並啟動要偵錯程式。  稍待片刻允許 DE 載入，或等到叫用中斷點。  
  
7.  第一個實例的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(您是專案\)，選取**附加至處理序**的**偵錯**功能表。  
  
8.  在**附加至處理序** 對話方塊中， **傳輸** 到 **遠端 \(僅限使用未驗證的機器碼\)**。  
  
9. 變更**限定詞**到您電腦的名稱 \(注意： 沒有歷程記錄的項目，因此您必須輸入這個名稱中只有一次\)。  
  
10. 在**可用的處理序** 清單中，選取執行個體正在執行，並按一下您 DE **附加** \] 按鈕。  
  
11. 您是在已載入的符號之後，請將中斷點置於 DE 的程式碼。  
  
12. 每次您停止並重新啟動偵錯的處理程序，請重複步驟 6 到 10。  
  
### 偵錯自訂專案型別  
  
1.  開始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在正常的登錄 hive，並載入您的專案輸入的專案 \(亦即，將來源與您的專案類型，無法為您的專案類型的執行個體化\)。  
  
2.  開啟專案屬性，然後移至**偵錯**頁面。  對於**命令**，輸入路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE \(根據預設，這是 *\[磁碟機\]*\\Program Files\\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\\Common7\\IDE\\devenv.exe\)。  
  
3.  對於**命令引數**，型別  `/rootsuffix exp` 的實驗性質的登錄 hive \(VSIP 安裝時建立\)。  
  
4.  按一下 \[**確定**\] 接受變更。  
  
5.  按下 F5 來啟動您的專案類型。  這會啟動的第二個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
6.  此時，您可以將中斷點置於您的專案類型的程式碼。  
  
7.  第二個執行個體中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 載入或建立您的專案類型的新執行個體。  在載入或建立時，可能會叫用中斷點。  
  
8.  偵錯您的專案類型。  
  
9. 如果您選擇的啟動 DE 程序進行偵錯，您就可以執行這些步驟之後啟動時，若您是要附加的 「 偵錯自訂偵錯引擎 」 程序中。  這會提供您三個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]執行： 一個用於您的專案類型的來源，另一個則用於您的執行個體化的專案類型和第三個連接到您的 DE。  
  
## 請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)