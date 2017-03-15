---
title: "列出記憶體命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory 命令"
  - "列出記憶體命令"
  - "ListMemory 命令"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 列出記憶體命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

顯示所指定記憶體範圍的內容。  
  
## 語法  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## 引數  
 `expression`  
 選擇項。  開始顯示記憶體的記憶體位址。  
  
## 參數  
 \/ANSI&#124;Unicode  
 選擇項。  將記憶體顯示為字元，對應 ANSI 或 Unicode 的記憶體位元組數。  
  
 \/Count:`number`  
 選擇項。  決定從 `expression` 開始要顯示多少記憶體位元組。  
  
 \/Format:`formattype`  
 選擇項。  在 \[**記憶體**\] 視窗中檢視記憶體資訊的格式類型，可以是 OneByte、TwoBytes、FourBytes、EightBytes、Float \(32 位元\) 或 Double \(64 位元\)。  如果使用 OneByte，則無法使用 `/Unicode`。  
  
 \/Hex&#124;Signed&#124;Unsigned  
 選擇項。  指定檢視數值的格式：帶正負號、不帶正負號，或十六進位。  
  
## 備註  
 除了寫出帶有所有參數的完整 **Debug.ListMemory** 命令外，您還可以使用帶有某些預設為指定值之參數的預設別名來叫用此命令。  例如，除了輸入：  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 您可以撰寫：  
  
```  
>df /Count:30 /Unicode  
```  
  
 這裡列出 **Debug.ListMemory** 命令可用之別名的清單︰  
  
|Alias|命令和參數|  
|-----------|-----------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory \/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## 範例  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## 請參閱  
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)   
 [列出執行緒命令](../../ide/reference/list-threads-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)