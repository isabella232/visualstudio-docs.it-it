---
title: 'Errore: Il processo di destinazione è stato terminato con codice di &#39;codice&#39; durante la valutazione della funzione &#39;funzione&#39; | Microsoft Docs'
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d82b6011a0dfa7f2c388e7d5f39a9ebabcd663
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850812"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Errore: Il processo di destinazione è stato terminato con codice di &#39;codice&#39; durante la valutazione della funzione &#39;(funzione)&#39;

Testo completo del messaggio: Il processo di destinazione è stato terminato con codice 'codice' durante la valutazione della funzione 'function'.

Per renderne più semplice controllare lo stato degli oggetti .NET, il debugger automaticamente forzerà il proseguimento del processo per eseguire codice aggiuntivo (in genere i metodi di richiamo di proprietà e `ToString` funzioni). Nella maggior parte degli scenari, queste funzioni completata correttamente o generano le eccezioni che possono essere rilevate dal debugger. Tuttavia, esistono alcune circostanze in cui non possono essere rilevate eccezioni perché superano i limiti del kernel, richiedono la distribuzione dei messaggi di utente o non sono recuperabili. Come un risultato, un getter della proprietà o metodo ToString che esegue codice in cui termina in modo esplicito il processo (ad esempio, chiama `ExitProcess()`) oppure genera un'eccezione non gestita che non può essere intercettata (ad esempio, `StackOverflowException`) terminerà il processo sottoposto a debug e fine della sessione di debug. Se si verifica questo messaggio di errore, ciò è accaduto.

Uno dei motivi comune per questo problema è che quando il debugger valuta una proprietà che chiama se stessa, questo può comportare un'eccezione di overflow dello stack. Non è possibile recuperare l'eccezione di overflow dello stack e terminerà il processo di destinazione.

## <a name="to-correct-this-error"></a>Per correggere l'errore

Esistono due possibili soluzioni al problema.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Soluzione 1 #. Impedire il debugger di chiamare la proprietà getter o il metodo ToString 

Il messaggio di errore indicherà il nome della funzione che il debugger ha tentato di chiamare. Con il nome della funzione, è possibile provare a ripetere la valutazione di tale funzione dal **Immediate** finestra per eseguire il debug della versione di valutazione. Il debug è possibile durante la valutazione dal **controllo immediato** finestra perché, a differenza delle valutazioni implicite dalle **Auto/variabili locali/espressione di controllo** windows, il debugger si interrompe in corrispondenza di eccezioni non gestite.

Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamata il getter della proprietà o `ToString` (metodo). Provare una delle operazioni seguenti:

* Modificare il metodo in un altro tipo di codice diverso da un getter della proprietà o metodo ToString e il problema non viene più visualizzato.
    -oppure-
* (Per `ToString`) definire un `DebuggerDisplay` attributo sul tipo e si può avere il debugger valuta un elemento diverso da `ToString`.
    -oppure-
* (Per un getter proprietà) Inserire il `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attributo della proprietà. Ciò può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità delle API, ma deve essere effettivamente un metodo.

Se non è possibile modificare questo metodo, è possibile interrompere il processo di destinazione in corrispondenza di un'istruzione alternativa e ripetere la valutazione.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Soluzione #2: Disabilitare tutte le valutazione implicita

Se le soluzioni precedenti non risolvono il problema, passare a **degli strumenti** > **opzioni**e deselezionare l'impostazione **debug**  >   **Generali** > **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**. Questo verrà disabilitata la maggior parte delle valutazioni di funzioni implicite e dovrebbe risolvere il problema.
