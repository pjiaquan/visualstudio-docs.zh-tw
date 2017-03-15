---
title: "RDT_ReadLock 使用量 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用量

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>是一個旗標，提供邏輯來鎖定文件中執行文件資料表 (RDT)，這 Visual Studio IDE 中目前開啟的所有文件的清單。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 這個旗標決定文件開啟時，以及文件是顯示在使用者介面或保留在記憶體中無形的方式。

一般而言，您會使用<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>的下列其中一個為 true 時︰</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- 當您想要開啟的文件，以隱藏和唯讀的但它尚未建立的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>應該是擁有人。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- 當您想要會提示您儲存的文件，以無形的方式開啟，使用者在 UI 中顯示，並將它關閉，則嘗試進行的使用者。

## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可見和不可見的文件

當使用者在 UI 中，開啟文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>文件的擁有者必須先建立和<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>必須設定旗標。</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 如果沒有<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>可以建立擁有者，則將不會儲存文件，當使用者按一下**全部儲存**或關閉 IDE。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 這表示如果文件就會開啟無形的方式修改在記憶體中，且使用者是系統提示您儲存文件在關閉或如果儲存**全部儲存**選擇時，則`RDT_ReadLock`無法使用。 相反地，您必須使用`RDT_EditLock`並註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>時<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>旗標。</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 和文件修改

先前所述的旗標表示將會產生不可見的文件開啟其`RDT_EditLock`文件開啟時使用者為可見**DocumentWindow**。 發生這種情況，使用者會看見**儲存**提示時可見**DocumentWindow**已關閉。 <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>使用的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服務一開始運作時只有`RDT_ReadLock`（亦即，當剖析資訊無形的方式開啟文件） 會採取。</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> 稍後，如果文件必須經過修改，然後鎖定會升級到較弱**RDT_EditLock**。 如果使用者再開啟文件中可見**DocumentWindow**、`CodeModel`的弱式`RDT_EditLock`發行。

如果使用者再關閉**DocumentWindow**選擇**否**當系統提示您儲存開啟的文件，然後在`CodeModel`實作處置的文件中的所有資訊，再重新從磁碟文件開啟無形的方式，將下一次需要文件的詳細資訊。 這個行為的微妙影響是在使用者開啟其中的執行個體**DocumentWindow**的不可見的開啟文件，加以修改，就會關閉它，並選擇**否**當系統提示您儲存文件。 在此情況下，如果文件`RDT_ReadLock`，然後將文件將不實際上會關閉，並修改過的文件會保持開啟狀態無形的方式在記憶體中，即使在使用者選擇不儲存文件。

如果看不見文件的開頭使用弱式`RDT_EditLock`，則它會產生其鎖定，當使用者開啟文件，明顯地，以及任何其他鎖定。 當使用者關閉**DocumentWindow**選擇**否**當系統提示您儲存文件，然後關閉文件必須可從記憶體。 這表示不可見的用戶端必須接聽 RDT 事件來追蹤發生這種情況。 下一次的文件是必要項目，必須重新開啟文件。
