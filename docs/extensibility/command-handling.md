---
title: "命令處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，傳統的命令處理"
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 命令處理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您的編輯器可以定義新的命令。 命令通常會顯示在功能表中，在工具列上，或在內容功能表中。  
  
 如需定義命令和功能表的詳細資訊，請參閱 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)。  
  
 語言服務可以控制哪些內容功能表會顯示在編輯器中，藉由攔截 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 列舉型別。 或者，您可以控制每個標記為基礎的內容功能表。 如需詳細資訊，請參閱 [語言服務篩選器的重要指令](../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>將命令加入至編輯器內容功能表  
 若要將命令加入至內容功能表中，您必須先定義一組屬於特定群組的功能表命令。 下列範例取自.vsct 檔產生部分的逐步解說為 [逐步解說︰ 加入功能與自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \< 功能表 guid ="guidCustomEditorCmdSet"id ="IDMX_RTF 」 優先順序 ="0x0000"type = 「 內容 」>  
  
 \< 父 guid ="guidCustomEditorCmdSet"id ="0"/>  
  
 \< 字串>  
  
 \< ButtonText>CustomEditor 內容功能表 \< / ButtonText>  
  
 \< CommandName>CustomEditorContextMenu \< / CommandName>  
  
 \< / 字串>  
  
 \< / 功能表>  
  
 \< / 功能表>  
  
 上述的文字加入內容功能表命令，以文字 **CustomEditor 內容功能表**。 功能表 GUID 是命令集的建立與此編輯器中，而且型別就是 「 內容 」。  
  
 您也可以使用預先定義的命令不需要在.vsct 檔中定義。 例如，如果您檢查 [Visual Studio 套件] 範本所產生的 EditorPane.cs 檔案，您會發現一組預先定義的命令，例如 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 所定義 <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, ，例如 onSelectAll 方法的命令處理常式中處理。  
  
## <a name="see-also"></a>請參閱  
 [命令、 功能表和工具列](../extensibility/internals/commands-menus-and-toolbars.md)