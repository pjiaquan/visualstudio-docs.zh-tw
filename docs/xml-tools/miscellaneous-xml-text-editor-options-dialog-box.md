---
title: "其他、XML、文字編輯器、選項對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 其他、XML、文字編輯器、選項對話方塊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此對話方塊可讓您變更 XML 編輯器的自動完成及結構描述設定。您可以從 \[工具\] 功能表中存取 \[選項\] 對話方塊。  
  
> [!NOTE]
>  當您選取 \[**文字編輯器**\] 資料夾、\[**XML**\] 資料夾，然後從 \[**選項**\] 對話方塊中選取 \[**其他**\] 選項時，就可以使用這些設定。  
  
## 自動插入  
 **關閉標記**  
 如果核取自動完成設定，當您鍵入右角括弧 \(\>\) 以關閉開始標記時，如果標記尚未關閉，編輯器會自動加入結束標記。這是預設行為。  
  
 空白項目的完成不會依賴自動完成設定。您可以隨時輸入反斜線 \(\/\) 以自動完成空白項目。  
  
 **屬性引號**  
 撰寫 XML 屬性時，編輯器會插入 `=" "` 字元，並將插入號 \(^\) 置於雙引號內。  
  
 預設會選取。  
  
 **命名空間宣告**  
 編輯器會自動在需要的位置插入命名空間宣告。  
  
 預設會選取。  
  
 **其他標記 \(註解、CDATA\)**  
 會自動完成註解、CDATA、DOCTYPE、處理指示及其他標記。  
  
 預設會選取。  
  
## 網路  
 **自動下載 DTD 及結構描述**  
 自動從 HTTP 位置下載結構描述及文件類型定義 \(DTD\)。此功能會使用已啟用自動 Proxy 伺服器偵測的 System.Net。  
  
 預設會選取。  
  
## 大綱  
 **檔案開啟時進入大綱模式**  
 會在檔案開始時開啟大綱功能。  
  
 預設會選取。  
  
## 快取  
 **結構描述**  
 指定結構描述快取的位置。瀏覽按鈕 \(**...**\) 會在目前結構描述快取位置開啟 \[目錄瀏覽\] 對話方塊。您可以選取其他目錄，或在對話方塊中選取資料夾，在資料夾上按一下滑鼠右鍵，並選擇 \[開啟\] 來查看目錄中的內容。  
  
## 請參閱  
 [XML 文件屬性 \(屬性視窗\)](../xml-tools/xml-document-properties-properties-window.md)   
 [XML 編輯器元件](../xml-tools/xml-editor-components.md)