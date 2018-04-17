---
title: 'Errore: Terminato il processo di destinazione durante la valutazione della funzione &#39;funzione&#39; | Documenti Microsoft'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: reference
f1_keywords:
- vs.debug.error.process_exit_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8dd6f0f47eb7160198d59e788096613da85e22f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="error-the-target-process-exited-while-evaluating-the-function-39function39"></a>Errore: Terminato il processo di destinazione durante la valutazione della funzione &#39;(funzione)&#39;

Testo del messaggio completo: il processo di destinazione è stato chiuso durante la valutazione della funzione 'function'. Vedere la finestra di Output per il codice di uscita del processo di destinazione.

Per rendere più semplice controllare lo stato degli oggetti .NET, il debugger automaticamente forzerà il processo sottoposto a debug per eseguire codice aggiuntivo (in genere i metodi di richiamo di proprietà e `ToString` funzioni). Nella maggior parte degli scenari, queste funzioni completata correttamente o generano eccezioni che possono essere intercettate dal debugger. Tuttavia, esistono alcune circostanze in cui le eccezioni non possono essere intercettate in quanto attraversano i limiti del kernel, richiedono la distribuzione dei messaggi utente oppure non sono recuperabili. Un risultato, un metodo Get della proprietà o del metodo ToString che esegue codice in cui termina in modo esplicito il processo (ad esempio, chiama `ExitProcess()`) o genera un'eccezione non gestita che non può essere intercettata (ad esempio, `StackOverflowException`) comporta la terminazione di processo sottoposto a debug e fine della sessione di debug. Se si verifica questo messaggio di errore, ciò è accaduto.
 
Uno dei motivi comune per questo problema è che quando il debugger valuta una proprietà che chiama se stessa, questo può comportare un'eccezione di overflow dello stack. Non è possibile recuperare l'eccezione di overflow dello stack e terminerà il processo di destinazione.
 
## <a name="to-correct-this-error"></a>Per correggere l'errore
 
Esistono due possibili soluzioni al problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Soluzione 1 #: Impedire il debugger di chiamare la proprietà di getter o il metodo ToString 

Il messaggio di errore indicherà il nome della funzione che il debugger ha tentato di chiamare. Con il nome della funzione, è possibile provare a valutare nuovamente tale funzione dal **immediato** finestra per eseguire il debug la valutazione. Il debug è possibile quando la valutazione dal **controllo immediato** finestra perché, a differenza delle valutazioni implicite dal **Auto/variabili locali/espressioni di controllo** windows, il debugger si interrompe su eccezioni non gestite.

Se è possibile modificare questa funzione, è possibile impedire il debugger potrà chiamare il metodo Get della proprietà o `ToString` metodo. Provare una delle operazioni seguenti:
 
* Modificare il metodo a un altro tipo di codice, oltre a una metodo Get della proprietà o metodo ToString e il problema non verrà più visualizzato.
    oppure
* (Per `ToString`) definire un `DebuggerDisplay` attributo nel tipo ed è possibile consentire al debugger di valutare un valore diverso da `ToString`.
    oppure
* (Per un getter di proprietà) Inserire il `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attributo sulla proprietà. Ciò può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità API, ma deve essere effettivamente un metodo.

Se non è possibile modificare questo metodo, è in grado di interrompere il processo di destinazione in corrispondenza di un'istruzione alternativa, quindi ripetere la valutazione.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Soluzione #2: Disabilitare tutti i valutazione implicita
 
Se le soluzioni precedenti non risolve il problema, passare a **strumenti** > **opzioni**e deselezionare l'impostazione **debug**  >   **Generale** > **Attiva valutazione delle proprietà e altre chiamate di funzioni implicite**. Questo disabiliterà la maggior parte delle valutazioni di funzioni implicite e dovrebbe risolvere il problema.



  
