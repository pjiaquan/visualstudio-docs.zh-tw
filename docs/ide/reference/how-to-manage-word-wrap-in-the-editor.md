---
title: "如何：管理編輯器中的自動換行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼編輯器, 自動換行"
  - "編輯器, 文字檢視"
  - "自動換行"
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：管理編輯器中的自動換行
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以設定並清除 \[**自動換行**\] 選項。  設定此選項後，一行很長的文字超出目前程式碼編輯器視窗寬度的部分，會顯示在下一行。  例如，當清除此選項時，可以加強行號的使用，您可以捲動到右邊以便查看長文字行的結尾部分。  
  
 如需詳細資訊，請參閱 [How to: Set General Editor Options](http://msdn.microsoft.com/zh-tw/704e4a7b-2162-4bed-8a47-f4f6ffec98c2)。  
  
> [!NOTE]
>  您所看到的對話方塊與功能表命令，可能會因您目前使用的設定與版本，而與 \[**說明**\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 程序  
  
#### 設定自動換行喜好設定  
  
1.  在 \[**工具**\] 功能表上，選取 \[**選項**\]。  
  
2.  在 \[**文字編輯器**\] 資料夾中，選擇 \[**所有語言**\] 子資料夾內之 \[**一般**\] 選項，將此選項設定為全域性。  
  
     \-或\-  
  
     在您用來進行程式設計的語言子資料夾內選擇 \[**一般**\] 選項。  
  
3.  在 \[**設定**\] 之下選取或清除 \[**自動換行**\] 選項。  
  
     選取 \[**自動換行**\] 選項以後，便會啟用 \[**顯示自動換行的視覺化圖像**\] 選項。  
  
4.  如果您偏好顯示出將長文字行自動換行至第二行的返回箭號指示器，請選取 \[**顯示自動換行的視覺化圖像**\] 選項。  假如您偏好不要顯示指示器箭號，請清除這個選項。  
  
    > [!NOTE]
    >  這些提醒箭號並未加入您的程式碼：僅用為顯示用途。  
  
## 請參閱  
 [自訂編輯器](../../ide/customizing-the-editor.md)   
 [文字編輯器選項對話方塊](../../ide/reference/text-editor-options-dialog-box.md)   
 [撰寫程式碼](../../ide/writing-code-in-the-code-and-text-editor.md)