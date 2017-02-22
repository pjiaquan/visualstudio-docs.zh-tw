---
title: "KeyBinding 項目 | Microsoft Docs"
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
  - "按鍵組合，VSCT XML 結構描述項目"
  - "KeyBinding 項目 (VSCT XML 結構描述)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# KeyBinding 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

KeyBinding 項目會指定命令的鍵盤快速鍵。  
  
 命令可以有單一和雙重按鍵繫結與其相關聯。 單一索引鍵繫結的範例是 CTRL \+ S 的 **儲存** 命令。 雙重的索引鍵繫結需要兩個連續的按鍵組合來觸發命令。 雙重繫結的範例是 CTRL \+ K、CTRL \+ K，若要設定書籤。  
  
## 語法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。|  
|id|必要項。|  
|編輯器|必要項。 編輯器 GUID 表示會使用此鍵盤快速鍵的編輯內容。 全域繫結範圍值是 「 guidVSStd97 」。|  
|key1|必要項。 有效值包括所有可輸入英數字元，以及加上 0 的 x 和 VK\_constants 兩位數十六進位值。|  
|mod1|選擇項。 CTRL、 ALT 及 shift 鍵，以空格分隔的任何組合。|  
|key2|選擇項。 有效值包括所有可輸入英數字元，以及加上 0 的 x 和 VK\_constants 兩位數十六進位值。|  
|mod2|選擇項。 CTRL、 ALT 及 shift 鍵，以空格分隔的任何組合。|  
|模擬器|選擇項。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|父代||  
|註釋||  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[按鍵組合的項目](../extensibility/keybindings-element.md)|群組鍵組項目和其他按鍵組合的群組。|  
  
## 範例  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## 請參閱  
 [按鍵組合的項目](../extensibility/keybindings-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)