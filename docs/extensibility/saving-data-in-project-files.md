---
title: "將資料儲存在專案檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "儲存專案檔中的資料 [Visual Studio]，"
  - "專案檔"
  - "專案檔，將資料儲存"
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# 將資料儲存在專案檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

專案子類型可以儲存並擷取子類型特定專案檔中的資料。  管理套件架構 \(MPF\) 提供兩個介面，以完成這項工作：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>介面允許存取屬性值，從**MSBuild**的專案檔的區段。  提供的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>可由任何使用者只要載入或儲存的使用者需要建置相關的資料。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>用來保存非建置在 XML 中自由格式的相關的資料。  提供的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>由呼叫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]需要保存非建置專案檔中的相關的資料。  
  
 如需有關如何將保存組建和非組建相關的資料的詳細資訊，請參閱[在 MSBuild 專案檔案中保存的資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。  
  
## 儲存和擷取組建相關的資料  
  
#### 若要儲存組建相關的專案檔中的資料  
  
-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法，將儲存的專案檔的完整路徑。  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### 若要擷取組建相關資料從專案檔  
  
-   呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A>方法以擷取專案檔的完整路徑。  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## 儲存和擷取非組建相關的資料  
  
#### 若要儲存非組建相關的專案檔中的資料  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A>方法，以判斷是否已變更 XML 片段，因為最後一次儲存到目前的檔案。  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法，將 XML 資料儲存在專案檔。  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### 若要擷取非組建相關的專案檔中的資料  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A>方法以初始化專案的擴充屬性和其他建置無關的資料。  如果沒有出現在專案檔的 XML 組態資料時，會呼叫這個方法。  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>方法，才能從專案檔中載入的 XML 資料。  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  本主題提供的所有程式碼範例是 「 組件的較大的範例中， [VSSDK 範例](../misc/vssdk-samples.md)。  
  
## 請參閱  
 [在 MSBuild 專案檔案中保存的資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)