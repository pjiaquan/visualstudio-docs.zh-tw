---
title: "進階編譯器設定對話方塊 (Visual Basic) | Microsoft Docs"
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
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "進階編譯器設定對話方塊"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
caps.handback.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 進階編譯器設定對話方塊 (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

請使用 \[**專案設計工具**\] 的 \[**進階編譯器設定**\] 對話方塊，指定專案的進階組建組態屬性。  此對話方塊只適用於 Visual Basic 專案。  
  
### 若要存取此對話方塊  
  
1.  在 \[**方案總管**\] 中，選取專案節點 \(不是 \[**方案**\] 節點\)。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  當 \[**專案設計工具**\] 出現時，請按一下 \[**編譯**\] 索引標籤。  
  
3.  在[專案設計工具、編譯頁 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) 上，選取 \[**組態**\] 和 \[**平台**\]。  \[**組態**\] 和 \[**平台**\] 清單不會顯示在簡化的組建組態中。  如需詳細資訊，請參閱[Debug and Release Project Configurations](http://msdn.microsoft.com/zh-tw/0440b300-0614-4511-901a-105b771b236e)。  
  
4.  按一下 \[**進階編譯選項**\]。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 最佳化  
 下列選項所指定的最佳化，在某些情況下可能會使程式檔案變得較小、程式執行速度變快，或是加速建置處理序。  
  
 **移除整數的溢位檢查**  
 根據預設，會清除這個核取方塊以啟用整數溢位檢查。  選取這個核取方塊移除整數的溢位檢查。  如果您選取這個核取方塊，整數計算可能會比較快。  不過，因此，如果您取消溢位檢查，而資料型別容量溢位，不正確的結果可能會儲存，而引發的錯誤。  
  
 如果發生溢位狀況會檢查和整數運算溢位，就會擲回 <xref:System.OverflowException> 例外狀況。  如果發生溢位狀況。不會檢查，整數運算溢位不會擲回例外狀況。  
  
 **啟用最佳化**  
 這個核取方塊預設為清除，表示停用編譯器最佳化。  若要啟用編譯器最佳化，則請選取這個核取方塊。  編譯器最佳化可使輸出檔更小、更快，而且更有效。  不過，，因為最佳化導致在輸出檔案中的程式碼重新整理，編譯器可以將偵錯困難。  
  
 **DLL 基底位址**  
 這個文字方塊會以十六進位格式顯示預設的 DLL 基底位址。  在類別庫和控制項程式庫專案中，您可以使用這個文字方塊指定當建立 DLL 時所使用的基底位址。  
  
 **產生偵錯資訊**  
 請從清單中選取 \[**無**\]、\[**完整**\] 或 \[**僅限 PDB**\]。  \[**無**\] 指定不要產生任何偵錯資訊，  \[**完整**\] 指定要產生完整的偵錯資訊，而 \[**僅限 PDB**\] 則指定只要產生 PDB 偵錯資訊。  根據預設，這個選項設定為 \[**完整**\]。  
  
## 編譯常數  
 條件式編譯常數有作用類似使用 [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) 前置處理器指示詞在原始程式檔，不過，定義的常數是公用和套用至專案中的所有檔案。  您可以使用 [\#If…Then…\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) 指示詞一起使用條件式編譯常數有條件地編譯原始程式檔。  請參閱 [Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)。  
  
 **定義 DEBUG 常數**  
 這個核取方塊預設為選取，表示要設定 DEBUG 常數。  
  
 **定義 TRACE 常數**  
 這個核取方塊預設為選取，表示要設定 TRACE 常數。  
  
 **自訂常數**  
 請在這個文字方塊中輸入應用程式的任何自訂常數。  輸入項目之間請以逗號分隔，格式如下：Name1\="Value1",Name2\="Value2",Name3\="Value3"。  
  
## 其他設定。  
 **產生序列化組件**  
 這個設定會指定編譯器是否會建立 XML 序列化組件。  如果您已經在程式碼中使用該類別將型別序列化，序列化組件可以改進 <xref:System.Xml.Serialization.XmlSerializer> 的啟動效能。  根據預設，這個選項設定為 \[**Auto**\]，指定只有當您已經在程式碼中使用 <xref:System.Xml.Serialization.XmlSerializer> 將型別編碼為 XML 時，才會產生序列化組件。  \[**Off**\] 則指定無論程式碼是否使用 <xref:System.Xml.Serialization.XmlSerializer>，永遠不會產生序列化組件。  \[**On**\] 則指定永遠會產生序列化組件。  序列化組件將命名為 `TypeName`.XmlSerializers.dll。  
  
## 請參閱  
 [專案設計工具、編譯頁 \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)