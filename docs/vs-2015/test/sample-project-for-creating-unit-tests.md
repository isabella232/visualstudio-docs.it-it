---
title: Progetto di esempio per la creazione di unit test | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: douge
ms.openlocfilehash: 846783e398fc07ef4ddfff4ea1bca05f840bca81
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529275"
---
# <a name="sample-project-for-creating-unit-tests"></a>Progetto di esempio per la creazione di unit test
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [progetto di esempio per la creazione di Unit test](https://docs.microsoft.com/visualstudio/test/sample-project-for-creating-unit-tests).  
  
Questo codice di esempio viene fornito per le procedure dettagliate seguenti:  
  
-   [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Questa procedura dettagliata descrive i passaggi per creare e personalizzare gli unit test, eseguirli ed esaminare i risultati dei test.  
  
-   [Procedura dettagliata: Esecuzione di test e visualizzazione di code coverage](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Questa procedura dettagliata illustra come visualizzare i dati di code coverage, che mostrano la percentuale di codice del progetto che si sta testando.  
  
-   [Procedura dettagliata: Uso dell'utilità di test della riga di comando](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). In questa procedura dettagliata è possibile usare l'utilità della riga di comando MSTest.exe per eseguire test e visualizzare i risultati.  
  
## <a name="sample-code"></a>Codice di esempio  
 L'unico errore intenzionale di questo esempio è che nel metodo Debit "m_balance += amount" dovrebbe esserci un segno meno e non più prima del segno di uguale.  
  
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
  
 /* Ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi è puramente casuale.  Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta. \*/  
  
## <a name="working-with-the-code"></a>Utilizzo del codice  
 Per usare questo codice, è necessario avere prima creato un progetto apposito in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Seguire i passaggi della sezione relativa alla preparazione per la procedura dettagliata in [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione ed esecuzione di unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Procedura dettagliata: Esecuzione di test e visualizzazione di code coverage](http://msdn.microsoft.com/en-us/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Procedura dettagliata: uso dell'utilità di test della riga di comando](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)


