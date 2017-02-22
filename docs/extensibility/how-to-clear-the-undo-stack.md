---
title: "如何: 清除復原堆疊 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，舊版-清除復原堆疊"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 清除復原堆疊
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列程序的下面將說明如何清除復原堆疊。  
  
### 若要清除復原堆疊  
  
1.  若要清除復原堆疊使用 [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) 方法。  以下是一個例子：  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## 請參閱  
 [How to: 實作復原管理](../extensibility/how-to-implement-undo-management.md)