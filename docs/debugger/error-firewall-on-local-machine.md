---
title: "錯誤：本機電腦的防火牆 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：本機電腦的防火牆
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本機電腦 \(也就是執行 Visual Studio 的電腦\) 上的網際網路連線防火牆，並未設定允許遠端偵錯。  針對使用預設傳輸的 Managed 或機器碼遠端偵錯，您必須為 DCOM 傳輸開啟 TCP 135 通訊埠。  您必須開啟檔案和印表機共用，並且必須將 devenv.exe 加入例外狀況清單。  可能也必須開啟某些 IPSEC 通訊埠。  
  
 如需詳細資訊，請參閱 [在裝置上設定遠端工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。