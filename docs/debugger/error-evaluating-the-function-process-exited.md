---
description: "Testo completo del messaggio: il processo di destinazione è terminato con il codice 'code' durante la valutazione della funzione 'function'."
title: Il processo di destinazione è stato terminato con codice &apos; di codice durante la valutazione della funzione &apos; &apos; &apos; | Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 680fc682c39ee919038da551a4d4cbbffbf6c168
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154495"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Errore: il processo di destinazione è stato terminato con codice &#39;codice&#39; durante la valutazione della funzione &#39;funzione&#39;

Testo completo del messaggio: il processo di destinazione è terminato con il codice 'code' durante la valutazione della funzione 'function'.

Per semplificare l'ispezione dello stato degli oggetti .NET, il debugger forza automaticamente il processo di debug a eseguire codice aggiuntivo (in genere metodi e funzioni del metodo get della `ToString` proprietà). Nella maggior parte degli scenari queste funzioni vengono completate correttamente o generano eccezioni che possono essere intercette dal debugger. Esistono tuttavia alcune circostanze in cui le eccezioni non possono essere intercette perché superano i limiti del kernel, richiedono il message pumping dell'utente o non sono irreversibili. Di conseguenza, un metodo Get o ToString della proprietà che esegue codice che termina in modo esplicito il processo (ad esempio, chiama ) o genera un'eccezione non gestita che non può essere intercettata (ad esempio , ) terminerà il processo di debug e terminerà la sessione `ExitProcess()` `StackOverflowException` di debug. Se viene visualizzato questo messaggio di errore, si è verificato questo errore.

Un motivo comune di questo problema è che quando il debugger valuta una proprietà che chiama se stesso, ciò può causare un'eccezione di overflow dello stack. Non è possibile recuperare l'eccezione di overflow dello stack e il processo di destinazione verrà terminato.

## <a name="to-correct-this-error"></a>Per correggere l'errore

Questo problema può essere risolto in due modi.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Soluzione #1: impedire al debugger di chiamare la proprietà getter o il metodo ToString 

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Con il nome della funzione, è possibile provare a  rivalutare tale funzione dalla finestra Controllo immediato per eseguire il debug della valutazione. Il debug è possibile quando  si esegue la valutazione dalla finestra Controllo immediato perché, a differenza delle valutazioni implicite dalle finestre **Auto/Variabili locali/Espressioni di** controllo, il debugger interrompe le eccezioni non gestite.

Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamare il metodo o il metodo get della `ToString` proprietà. Provare a eseguire una delle operazioni seguenti:

* Modificare il metodo in un altro tipo di codice oltre a un metodo get della proprietà o ToString e il problema non verrà risolto.
    -oppure-
* (Per `ToString` ) Definire un attributo sul tipo ed è possibile fare in modo `DebuggerDisplay` che il debugger valuti un valore diverso da `ToString` .
    -oppure-
* (Per un getter di proprietà) Inserire `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` l'attributo nella proprietà . Questo può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità dell'API, ma deve essere effettivamente un metodo.

Se non è possibile modificare questo metodo, è possibile interrompere il processo di destinazione in corrispondenza di un'istruzione alternativa e ripetere la valutazione.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Soluzione #2: disabilitare tutte le valutazioni implicite

Se le soluzioni precedenti non consentono di risolvere il problema, passare a Opzioni degli strumenti e deselezionare l'impostazione Debug generale Abilita valutazione proprietà e  >  altre chiamate di   >    >  **funzione implicite**. In questo modo la maggior parte delle valutazioni delle funzioni implicite verrà disabilitata e il problema verrà risolto.
