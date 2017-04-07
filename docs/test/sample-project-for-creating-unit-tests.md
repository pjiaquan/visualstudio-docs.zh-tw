---
title: "用於建立單元測試的範例專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
ms.author: douge
manager: douge
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 85a4222db883846e2da0bb64b4c39be1e737dcd2
ms.lasthandoff: 02/22/2017

---
# <a name="sample-project-for-creating-unit-tests"></a>用於建立單元測試的範例專案
所提供的這個範例程式碼可用於下列逐步解說：  
  
-   [逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)。 此逐步解說會引導您逐步完成建立及自訂單元測試、加以執行，以及檢查測試結果。  
  
-   [逐步解說：執行測試並檢視程式碼涵蓋範圍](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)。 此逐步解說將說明如何檢視程式碼涵蓋範圍資料，該資料會顯示專案程式碼中正在受測試的部分。  
  
-   [逐步解說：使用命令列測試公用程式](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)。 在此逐步解說中，您可以使用 MSTest.exe 命令列公用程式來執行測試及檢視結果。  
  
## <a name="sample-code"></a>程式碼範例  
 此範例中唯一刻意設計的錯誤是在 Debit 方法 "m_balance += amount" 中，等號前面應該是減號，而不是加號。  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 /* 此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。  並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。 \*/  
  
## <a name="working-with-the-code"></a>使用程式碼  
 若要使用此程式碼，您必須先在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中為其建立專案。 請遵循[逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)中＜準備逐步解說＞一節的步驟。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：針對 Managed 程式碼建立和執行單元測試](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [逐步解說：執行測試並檢視程式碼涵蓋範圍](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [逐步解說：使用命令列測試公用程式](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)

