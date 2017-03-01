---
title: "IDE 定義的命令，來擴充專案系統 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE 定義的命令，來擴充專案系統
當您想要擴充專案系統時，您可以使用命令和命令所提供的群組[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 下列各節列出命令特別適合用於擴充專案系統的項目。  
  
## <a name="command-menus"></a>功能表命令  
 下表顯示有用的位置，以叫用專案擴充性的高階命令放命令功能表。  
  
|命令功能表|說明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**專案**最上層的功能表。|  
|IDM_VS_TOOL_PROJWIN|**方案總管 中**工具列。|  
  
## <a name="shortcut-menus"></a>快顯功能表  
 下表顯示快顯功能表中選取單一節點時所要套用**方案總管 中**，或有多個同質性的選取項目中時**方案總管 中**，這是相同型別的所有選取的節點時。  
  
|快顯功能表|描述|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|適用於選取專案節點時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|選取檔案時適用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|適用於選取資料夾時。|  
|IDM_VS_CTXT_WEBREFFOLDER|適用於選取 [Web 參考] 資料夾時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|適用於選取參考根節點，稱為 「 參考 」 時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|適用於選取參考節點。這些包括組件、 COM 和只專案參考。 不包含 Web 參考。|  
  
 下表顯示當套用的快顯功能表中的選取**方案總管 中**跨越多個階層，  
  
|快顯功能表|說明|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|適用於目前的選取範圍包含方案節點和根專案節點時。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|適用於目前的選取範圍包含方案節點和專案項目時。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|適用於當目前的選取範圍包含多個專案只限根節點。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|當目前的選取範圍包含根專案節點和專案項目時套用。 此外，範圍可能包含方案節點。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|適用於目前的選取範圍包含在方案中，多個專案中的專案項目時，或在相同專案中選取不同類型的項目。|  
  
## <a name="command-groups"></a>命令群組  
 下表顯示當擴充專案，而且您可以透過存取時，您可以使用的命令群組<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>快顯功能表。</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|命令群組|說明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|建立、 重建和部署專案的命令。|  
|IDG_VS_CTXT_COMPILELINK|編譯和連結專案的指令。|  
|IDG_VS_CTXT_PROJECT_CONFIG|設定專案組態和建置順序的命令。|  
|IDG_VS_CTXT_PROJECT_ADD|將項目加入至專案的命令。|  
|IDG_VS_CTXT_PROJECT_START|設定啟始專案 F5 索引鍵相關聯的命令。|  
|IDG_VS_CTXT_PROJECT_SAVE|儲存專案項目的命令。|  
|IDG_VS_CTXT_PROJECT_DEBUG|偵錯的指令。|  
|IDG_VS_CTXT_PROJECT_SCC|原始檔控制命令。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|剪下 命令複製並貼上作業。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供存取權的命令**專案屬性**對話方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand 對比OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)
