---
title: "專案設計工具、建置事件 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "建置事件"
  - "專案設計工具, [建置事件] 頁面"
  - "建置前事件"
  - "建置後事件"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 專案設計工具、建置事件 (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

請使用 \[**專案設計工具**\] 的 \[**建置事件**\] 頁，指定組建組態指令。  您還可以在這裡指定執行建置後事件的條件。  如需詳細資訊，請參閱 [如何：指定建置事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md) 和 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)。  
  
## UIElement 清單  
 **組態**  
 在此頁面中無法編輯這個控制項。  如需這個控制項的說明，請參閱[專案設計工具、建置頁 \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **平台**  
 在此頁面上無法編輯這個控制項。  如需這個控制項的說明，請參閱[專案設計工具、建置頁 \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **建置前事件命令列**  
 指定任何要在建置開始前執行的命令。  如果要輸入的命令很長，請按一下 \[**建置前進行編輯**\] 以顯示[建置前事件\/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
> [!NOTE]
>  如果專案是最新的且未觸發任何建置，則不會執行建置前事件。  
  
 **建置後事件命令列**  
 指定任何要在建置結束後執行的命令。  如果要輸入的命令很長，請按一下 \[**建置後進行編輯**\] 以顯示 \[**建置前事件\/建置後事件命令列**\] 對話方塊。  
  
> [!NOTE]
>  在執行 .bat 檔的所有建置後命令之前加入 `call` 陳述式。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **執行建置後事件**  
 指定下表中的條件，以執行建置後事件。  
  
|選項|結果|  
|--------|--------|  
|**永遠**|不論是否建置成功，建置後事件都將執行。|  
|**建置成功時**|如果建置成功，建置後事件才會執行。  因此，只要建置成功，該事件甚至會為最新的專案執行。|  
|**當組建更新專案輸出時**|只有當編譯器的輸出檔 \(.exe 或 .dll\) 與之前的編譯器輸出檔不同時，建置後事件才會執行。  因此，專案如果是最新的，建置後事件便不會執行。|  
  
## 請參閱  
 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [如何：指定建置事件 \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [專案屬性參考](../../ide/reference/project-properties-reference.md)   
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md)