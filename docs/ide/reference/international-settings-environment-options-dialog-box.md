---
title: "選項對話方塊、環境、國際設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "國際設定對話方塊"
  - "語言, 環境設定"
  - "[選項] 對話方塊, 國際設定"
  - "語言, 指定預設值"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 選項對話方塊、環境、國際設定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您在電腦上安裝多個語言版本的整合式開發環境 \(IDE\) 時，\[國際設定\] 頁面可讓您變更預設語言。  您可以從 \[工具\] 功能表選取 \[選項\]，然後從 \[環境\] 資料夾選擇 \[國際設定\]，來存取這個對話方塊。  如果此頁面未出現在清單中，請在 \[**選項**\] 對話方塊中選取 \[**顯示所有設定**\]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 \[說明\] 中描述的有所不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 **語言**  
 列出已安裝產品語言版本的可用語言。  除非您在電腦上安裝多個語言版本，否則無法使用這個選項。  如果產品的多個語言或產品的混合語言安裝共用環境，這個 \[語言\] 區段會變更為 \[與 Microsoft Windows 相同\]。  
  
> [!CAUTION]
>  在安裝了多個語言的系統中，Visual C\+\+ 建置工具 \(cl.exe、link.exe、nmake.exe、bscmake.exe 和相關檔案\) 不會受到這項設定的影響。  由於 Visual C\+\+ 建置工具不會使用附屬 DLL 模型，因此這些工具會使用最後一個安裝的語言版本，而且之前安裝的語言版本工具會遭到覆寫。  
  
## 請參閱  
 [安裝多個語言版本的 Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [環境選項對話方塊](../../ide/reference/environment-options-dialog-box.md)