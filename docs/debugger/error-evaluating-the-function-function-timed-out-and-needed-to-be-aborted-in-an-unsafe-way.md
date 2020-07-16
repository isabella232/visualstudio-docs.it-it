---
title: Errore-la valutazione della funzione &#39;della funzione&#39; scaduta e deve essere interrotta in modo non sicuro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a655e2994e1eaa1c5ac65e7b8782ec5b9d6f72
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386719"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Errore: si è verificato un timeout durante la valutazione della funzione &#39;funzione&#39; e l'operazione deve essere interrotta in modo non sicuro

Testo del messaggio completo: si è verificato un timeout durante la valutazione della funzione ' Function ', che deve essere interrotta in modo non sicuro. Questo potrebbe aver danneggiato il processo di destinazione.

Per semplificare l'ispezione dello stato degli oggetti .NET, il debugger forza automaticamente il processo sottoposto a debug a eseguire codice aggiuntivo, in genere metodi di richiamo di proprietà e funzioni ToString. Nella maggior parte dei casi, queste funzioni vengono completate rapidamente e semplificano notevolmente il debug. Tuttavia, il debugger non esegue l'applicazione in un ambiente sandbox. Di conseguenza, un metodo Get o ToString della proprietà che chiama una funzione nativa che smette di rispondere può causare timeout lunghi che potrebbero non essere ripristinabili. Se viene visualizzato questo messaggio di errore, si è verificato il problema.

Una causa comune di questo problema è che quando il debugger valuta una proprietà, consente solo l'esecuzione del thread controllato. Quindi, se la proprietà è in attesa dell'esecuzione di altri thread all'interno dell'applicazione sottoposta a debug e se è in attesa in un modo in cui il Runtime .NET non è in grado di interrompere, questo problema si verificherà.

## <a name="to-correct-this-error"></a>Per correggere l'errore

Questo problema può essere dovuto a diverse soluzioni.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1 soluzione: impedire al debugger di chiamare la proprietà Getter o il metodo ToString

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamare il metodo Get o ToString della proprietà. Provare una delle operazioni seguenti:

* Modificare il metodo in un altro tipo di codice oltre a un metodo getter o ToString per la proprietà e il problema non è più possibile.
    -oppure-
* (Per ToString) Definire un attributo DebuggerDisplay per il tipo ed è possibile fare in modo che il debugger valuti un valore diverso da ToString.
    -oppure-
* (Per un getter di proprietà) Inserire l' `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attributo sulla proprietà. Questa operazione può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità con le API, ma deve essere effettivamente un metodo.

### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>#2 soluzione: fare in modo che il codice di destinazione chieda al debugger di interrompere la valutazione

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Se il metodo di richiamo della proprietà o ToString a volte non viene eseguito correttamente, soprattutto nelle situazioni in cui il codice richiede un altro thread per eseguire il codice, la funzione di implementazione può chiamare `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` per chiedere al debugger di interrompere la valutazione della funzione. Con questa soluzione è comunque possibile valutare in modo esplicito queste funzioni, ma il comportamento predefinito è che l'esecuzione si interrompe quando si verifica la chiamata NotifyOfCrossThreadDependency.

### <a name="solution-3-disable-all-implicit-evaluation"></a>#3 soluzione: disabilitare tutta la valutazione implicita

Se le soluzioni precedenti non consentono di risolvere il problema, passare a **strumenti**  >  **Opzioni**e deselezionare l'impostazione **debug**  >  **generale**  >  **Abilita valutazione delle proprietà e altre chiamate di funzioni implicite**. Questa operazione Disabilita la maggior parte delle valutazioni di funzioni implicite e dovrebbe risolvere il problema.

### <a name="solution-4-enable-managed-compatibility-mode"></a>#4 soluzione: abilitare la modalità di compatibilità gestita

Se si passa al motore di debug legacy, potrebbe essere possibile eliminare l'errore. Passare a **strumenti**  >  **Opzioni**e selezionare l'impostazione **debug**  >  **generale**  >  **Usa modalità di compatibilità gestita**. Per ulteriori informazioni, vedere [Opzioni di debug generali](../debugger/general-debugging-options-dialog-box.md).
