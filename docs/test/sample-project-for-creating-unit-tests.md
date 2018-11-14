---
title: Esempio di codice per la creazione di unit test
description: Questo articolo illustra un codice di esempio che può essere testato con gli unit test in Visual Studio.
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deddf46a479e0ab8d4e0bebbaf3fffe4d90b622d
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293447"
---
# <a name="sample-code-for-testing"></a>Codice di esempio per i test

Questo codice di esempio contiene una classe, *BankAccount*, con vari metodi che possono essere testati usando gli unit test.

Il codice viene usato nelle procedure dettagliate seguenti:

- [Creare ed eseguire unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Questa procedura dettagliata descrive i passaggi per creare e personalizzare gli unit test, eseguirli ed esaminare i risultati dei test.
- [Uso dell'utilità di test della riga di comando](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). In questa procedura dettagliata è possibile usare l'utilità della riga di comando *MSTest.exe* per eseguire test e visualizzare i risultati.

## <a name="sample-code"></a>Codice di esempio

L'unico errore intenzionale di questo esempio è che nel metodo Debit "m_balance += amount" dovrebbe esserci un segno meno e non più prima del segno di uguale.

```csharp
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

/* Ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi è puramente casuale. Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta. \*/

## <a name="create-the-project"></a>Creare il progetto

Per usare questo codice, creare prima un progetto apposito in Visual Studio. Seguire i passaggi per la creazione del progetto in [Procedura dettagliata: Creare ed eseguire unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creare ed eseguire unit test per codice gestito](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Procedura dettagliata: Uso dell'utilità di test della riga di comando](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
