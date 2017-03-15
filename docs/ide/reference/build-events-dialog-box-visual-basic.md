---
title: "建置事件對話方塊 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "建置事件"
  - "建置事件, 指定"
  - "建置前事件"
  - "[建置事件] 對話方塊"
  - "建置後事件"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# 建置事件對話方塊 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

請使用 \[**建置事件**\] 對話方塊，指定組建組態指令。  您也可以在這裡指定執行建置前或建置後事件的條件。  如需詳細資訊，請參閱 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)。  
  
 **建置前事件命令列**  
 指定任何要在建置開始前執行的命令。  如果要輸入的命令很長，請按一下 \[**建置前進行編輯**\] 以顯示[建置前事件\/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)。  
  
> [!NOTE]
>  如果是最新的專案且未觸發任何建置，則建置前事件將不會執行。  
  
 **建置後事件命令列**  
 指定任何要在建置結束後執行的命令。  如果要輸入的命令很長，請按一下 \[**建置後進行編輯**\] 以顯示 \[**建置前事件\/建置後事件命令列**\] 對話方塊。  
  
> [!NOTE]
>  在執行 .bat 檔的所有建置後命令之前加入 `call` 陳述式。  例如，`call C:\MyFile.bat` 或 `call C:\MyFile.bat call C:\MyFile2.bat`。  
  
 **執行建置後事件**  
 指定下表中的條件，以執行建置後事件。  
  
|選項|結果|  
|--------|--------|  
|**永遠**|不論是否建置成功，建置後事件都將執行。|  
|**建置成功時**|如果建置成功，建置後事件才會執行。  因此，只要建置成功，即使是最新的專案，該事件也會執行。  這是預設值。|  
|**當組建更新專案輸出時**|只有當編譯器的輸出檔 \(.exe 或 .dll\) 與之前的編譯器輸出檔不同時，建置後事件才會執行。  因此，如果專案是最新的，建置後事件便不會執行。|  
  
## 請參閱  
 [專案設計工具、編譯頁 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [如何：指定建置事件 \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [建置前事件\/建置後事件命令列對話方塊](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)