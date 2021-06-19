---
title: La valutazione della funzione ha avuto un timeout e deve essere interrotta in modo non sicuro | &apos; &apos; Microsoft Docs
description: "Testo completo del messaggio: si è verificata la valutazione del timeout della funzione 'function' che deve essere interrotta in modo non sicuro."
ms.date: 06/18/2021
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e928bb0ebae1e644729fcaf4f47b7dd461399be6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386670"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Errore: la valutazione della funzione &#39;funzione&#39; timeout e deve essere interrotta in modo non sicuro

Testo completo del messaggio: si è verificata la valutazione del timeout della funzione 'function' che deve essere interrotta in modo non sicuro. Il processo di destinazione potrebbe essere danneggiato.

Per semplificare l'analisi dello stato degli oggetti .NET, il debugger forza automaticamente il processo di debug a eseguire codice aggiuntivo (in genere i metodi get della proprietà e le funzioni ToString). Nella maggior parte degli scenari queste funzioni vengono completate rapidamente e semplificano affatto il debug. Tuttavia, il debugger non esegue l'applicazione in una sandbox. Di conseguenza, un metodo Get o ToString della proprietà che chiama in una funzione nativa che smette di rispondere può causare timeout lunghi che potrebbero non essere recuperabili. Se viene visualizzato questo messaggio di errore, si è verificato questo errore.

Un motivo comune di questo problema è che quando il debugger valuta una proprietà, consente solo l'esecuzione del thread esaminato. Pertanto, se la proprietà è in attesa dell'esecuzione di altri thread all'interno dell'applicazione di cui è stato eseguito il debug e se è in attesa in un modo che il runtime .NET non è in grado di interrompere, questo problema si verifica.

## <a name="to-correct-this-error"></a>Per correggere l'errore

Vedere le sezioni seguenti per diverse possibili soluzioni a questo problema.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Soluzione #1: impedire al debugger di chiamare la proprietà getter o il metodo ToString

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Se è possibile modificare questa funzione, è possibile impedire al debugger di chiamare il metodo getter della proprietà o ToString. Provare a eseguire una delle operazioni seguenti:

* Modificare il metodo in un altro tipo di codice oltre a un metodo get della proprietà o ToString e il problema non verrà risolto.
  -oppure-
* (Per ToString) Definire un [attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) sul tipo ed è possibile fare in modo che il debugger valuti un valore diverso da ToString.
  -oppure-
* (Per un getter di proprietà) Inserire [l'attributo System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) nella proprietà . Ciò può essere utile se si dispone di un metodo che deve rimanere una proprietà per motivi di compatibilità dell'API, ma deve essere effettivamente un metodo.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Soluzione #2: chiedere al debugger di interrompere la valutazione con il codice di destinazione

Il messaggio di errore indica il nome della funzione che il debugger ha tentato di chiamare. Se a volte il metodo getter o ToString della proprietà non viene eseguito correttamente, soprattutto nei casi in cui il problema è che il codice richiede un altro thread per eseguire il codice, la funzione di implementazione può chiamare [System.Diagnostics.Debugger.NotifyOfCrossThreadDependency](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) per chiedere al debugger di interrompere la valutazione della funzione. Con questa soluzione è comunque possibile valutare in modo esplicito queste funzioni, ma il comportamento predefinito è che l'esecuzione si arresta quando si verifica la chiamata NotifyOfCrossThreadDependency.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Soluzione #3: disabilitare tutte le valutazioni implicite

Se le soluzioni precedenti non consentono di risolvere il problema, passare a Opzioni degli strumenti e deselezionare l'impostazione Debug generale Abilita valutazione proprietà e  >  altre chiamate di   >    >  **funzione implicite**. In questo modo la maggior parte delle valutazioni delle funzioni implicite verrà disabilitata e il problema verrà risolto.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Soluzione #4: Verificare la compatibilità con gli strumenti di sviluppo di terze parti

Se si usa Resharper, vedere questo [problema per](https://youtrack.jetbrains.com/issue/RSRP-476824) suggerimenti.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Soluzione #5: abilitare la modalità di compatibilità gestita

Se si passa al motore di debug legacy, è possibile eliminare questo errore. Passare a **Opzioni**  >  **degli strumenti** e selezionare l'impostazione **Debug**  >  **Generale**  >  **Usa modalità di compatibilità gestita**. Per altre informazioni, vedere [Opzioni di debug generali](../debugger/general-debugging-options-dialog-box.md).
