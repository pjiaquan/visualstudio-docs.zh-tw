---
title: "示範範例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼分析, 範例"
  - "示範範例 [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 示範範例
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下列程序將說明如何建立[逐步解說：分析 C\/C\+\+ 程式碼的缺失](../Topic/Walkthrough:%20Analyzing%20C-C++%20Code%20for%20Defects.md)的範例。  此程序會建立：  
  
-   名為 CppDemo 的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案。  
  
-   名為 CodeDefects 的靜態程式庫專案。  
  
-   名為 Annotations 的靜態程式庫專案。  
  
 此程序也會提供靜態程式庫標頭和 .cpp 檔的程式碼。  
  
### 建立 CppDemo 方案和 CodeDefects 專案  
  
1.  按一下 \[**檔案**\] 功能表，指向 \[**新增**\]，然後按一下 \[**新增專案**\]。  
  
2.  在 \[**專案類型**\] 樹狀清單中，如果 Visual C\+\+ 不是 VS 中的預設語言，請展開 \[**其他語言**\]。  
  
3.  展開 \[**Visual C\+\+**\]，然後按一下 \[**一般**\]。  
  
4.  按一下 \[**範本**\] 中的 \[**空專案**\]。  
  
5.  在 \[**名稱**\] 文字方塊中，輸入 **CodeDefects**。  
  
6.  選取 \[**為方案建立目錄**\] 核取方塊。  
  
7.  在 \[**方案名稱**\] 文字方塊中，輸入 **CppDemo**。  
  
### 將 CodeDefects 專案設定為靜態程式庫  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**CodeDefects**\]，然後按一下 \[**屬性**\]。  
  
2.  展開 \[**組態屬性**\]，然後按一下 \[**一般**\]。  
  
3.  在 \[**一般**\] 清單中，選取 \[**目標副檔名**\] 旁邊欄中的文字，然後輸入 **.lib**。  
  
4.  在 \[**專案預設值**\] 中，按一下 \[**組態型別**\] 旁邊的欄，然後按一下 \[**靜態程式庫 \(.lib\)**\]。  
  
### 將標頭和原始程式檔加入至 CodeDefects 專案  
  
1.  在 \[方案總管\] 中，展開 \[**CodeDefects**\]，以滑鼠右鍵按一下 \[**標頭檔**\]，然後按一下 \[**加入**\]，再按一下 \[**新項目**\]。  
  
2.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**程式碼**\]，然後按一下 \[**標頭檔 \(.h\)**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 **Bug.cpp**，然後按一下 \[**加入**\]。  
  
4.  複製下列程式碼並將其貼入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 編輯器中的 **Bug.cpp** 檔。  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**原始程式檔**\]，指向 \[**新增**\]，再按一下 \[**新項目**\]。  
  
6.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**C\+\+ 檔 \(.cpp\)**\]。  
  
7.  在 \[**名稱**\] 方塊中，輸入 **Bug.cpp**，然後按一下 \[**加入**\]。  
  
8.  複製下列程式碼並將其貼入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 編輯器中的 Bug.h 檔。  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. 按一下 \[**檔案**\] 功能表，然後按一下 \[**全部儲存**\]。  
  
### 加入 Annotations 專案並設定為靜態程式庫  
  
1.  在 \[方案總管\] 中，按一下 \[**CppDemo**\]，指向 \[**加入**\]，然後按一下 \[**新增專案**\]。  
  
2.  在 \[**加入新的專案**\] 對話方塊中，展開 \[Visual C\+\+\]，然後按一下 \[**一般**\]，再按一下 \[**空專案**\]。  
  
3.  在 \[**名稱**\] 文字方塊中，輸入 **Annotations**，然後按一下 \[**加入**\]。  
  
4.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**Annotations**\]，然後按一下 \[**屬性**\]。  
  
5.  展開 \[**組態屬性**\]，然後按一下 \[**一般**\]。  
  
6.  在 \[**一般**\] 清單中，選取 \[**目標副檔名**\] 旁邊欄中的文字，然後輸入 **.lib**。  
  
7.  在 \[**專案預設值**\] 中，按一下 \[**組態型別**\] 旁邊的欄，然後按一下 \[**靜態程式庫 \(.lib\)**\]。  
  
### 將標頭檔和原始程式檔加入至 Annotations 專案  
  
1.  在 \[方案總管\] 中，展開 \[**Annotations**\]，以滑鼠右鍵按一下 \[**標頭檔**\]，然後按一下 \[**加入**\]，再按一下 \[**新項目**\]。  
  
2.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**標頭檔 \(.h\)**\]。  
  
3.  在 \[**名稱**\] 方塊中，輸入 **annotations.h**，然後按一下 \[**加入**\]。  
  
4.  複製下列程式碼並將其貼入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 編輯器中的 **annotations.h** 檔。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**原始程式檔**\]，指向 \[**新增**\]，再按一下 \[**新項目**\]。  
  
6.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**程式碼**\]，然後按一下 \[**C\+\+ 檔 \(.cpp\)**\]。  
  
7.  在 \[**名稱**\] 方塊中，輸入 **annotations.cpp**，再按 \[**加入**\]。  
  
8.  複製下列程式碼並將其貼入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 編輯器中的 **annotations.cpp** 檔。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. 按一下 \[**檔案**\] 功能表，然後按一下 \[**全部儲存**\]。