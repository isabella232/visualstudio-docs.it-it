---
title: Il processo di destinazione è stato terminato con codice codice &apos; &apos; durante la valutazione della &apos; funzione Function &apos; | Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07891e5bcbcab35a4ec5652676a014b87dd32d43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871637"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Errore: il processo di destinazione è stato terminato con codice &#39;codice&#39; durante la valutazione della funzione &#39;funzione&#39;

Testo completo del messaggio: il processo di destinazione è stato terminato con il codice ' code ' durante la valutazione della funzione ' Function '.

Per semplificare l'analisi dello stato degli oggetti .NET, il debugger forza automaticamente il processo sottoposto a debug a eseguire codice aggiuntivo (in genere metodi e funzioni getter di proprietà `ToString` ). Nella maggior parte degli scenari queste funzioni vengono completate correttamente o generano eccezioni che possono essere rilevate dal debugger. In alcune circostanze, tuttavia, non è possibile intercettare le eccezioni perché superano i limiti del kernel, richiedono la distribuzione dei messaggi utente o sono irreversibili. Di conseguenza, un metodo Get o ToString della proprietà che esegue codice che termina in modo esplicito il processo (ad esempio, chiama `ExitProcess()` ) o genera un'eccezione non gestita che non può essere intercettata (ad esempio, `StackOverflowException` ) termina il processo sottoposto a debug e termina la sessione di debug. Se viene visualizzato questo messaggio di errore, si è verificato il problema.

Una causa comune di questo problema è che quando il debugger valuta una proprietà che chiama se stessa, è possibile che venga generata un'eccezione di overflow dello stack. Non è possibile recuperare l'eccezione di overflow dello stack e il processo di destinazione verrà terminato.

## <a name="to-correct-this-error"></a>Per correggere l'errore

Esistono due possibili soluzioni per questo problema.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1 soluzione: impedire al debugger di chiamare la proprietà Getter o il metodo ToString 

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Con il nome della funzione, è possibile provare a rivalutare la funzione dalla finestra di **controllo immediato** per eseguire il debug della valutazione. È possibile eseguire il debug durante la valutazione dalla finestra di **controllo immediato** perché, a differenza delle valutazioni implicite dalle finestre **auto/variabili locali/espressioni di controllo** , il debugger si interrompe in caso di eccezioni non gestite.

Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamare il metodo o il metodo Get della proprietà `ToString` . Provare una delle operazioni seguenti:

* Modificare il metodo in un altro tipo di codice oltre a un metodo getter o ToString per la proprietà e il problema non è più possibile.
    -oppure-
* (Per `ToString` ) Definire un `DebuggerDisplay` attributo per il tipo ed è possibile fare in modo che il debugger valuti un valore diverso da `ToString` .
    -oppure-
* (Per un getter di proprietà) Inserire l' `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attributo sulla proprietà. Questa operazione può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità con le API, ma deve essere effettivamente un metodo.

Se non è possibile modificare questo metodo, potrebbe essere possibile suddividere il processo di destinazione in un'istruzione alternativa e ripetere la valutazione.

### <a name="solution-2-disable-all-implicit-evaluation"></a>#2 soluzione: disabilitare tutta la valutazione implicita

Se le soluzioni precedenti non consentono di risolvere il problema, passare a **strumenti**  >  **Opzioni** e deselezionare l'impostazione **debug**  >  **generale**  >  **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**. Questa operazione Disabilita la maggior parte delle valutazioni di funzioni implicite e dovrebbe risolvere il problema.
