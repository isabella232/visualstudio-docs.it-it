---
title: JIT debug e ottimizzazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8699c468a3bf5f9c72131add984055f08f23c7c3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959291"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
**Funzionano delle ottimizzazioni in .NET:** Se si sta tentando di eseguire il debug di codice, è più semplice quando che il codice è **non** ottimizzato. Questo avviene perché quando il codice è ottimizzato, il compilatore e il runtime di apportare modifiche al codice della CPU generato in modo che viene eseguito più velocemente, ma ha un mapping diretto meno a codice sorgente originale. Ciò significa che i debugger sono spesso non è possibile indicare il valore delle variabili locali e l'esecuzione di istruzioni del codice e i punti di interruzione potrebbe non funzionare come previsto.

In genere la configurazione della build di rilascio crea codice ottimizzato e non la configurazione di build di Debug. Il `Optimize` proprietà di MSBuild controlla se viene indicato al compilatore di ottimizzare il codice.

Nell'ecosistema .NET, codice è abilitato dall'origine di istruzioni CPU in un processo in due fasi: innanzitutto, il C# compilatore converte il testo digitato in un formato binario intermedio denominato codice MSIL e si scrive in file con estensione dll. In un secondo momento, il Runtime di .NET converte il codice MSIL in istruzioni CPU. Consente di ottimizzare entrambi questi passaggi per un certo livello, ma il secondo passaggio eseguito dal Runtime di .NET esegue le ottimizzazioni più significative.

**L'opzione 'Disattivare l'ottimizzazione JIT al caricamento del modulo (solo gestito)':** Il debugger è disponibile un'opzione che controlla cosa accade quando una DLL che viene compilata con ottimizzazioni abilitate Carica all'interno del processo di destinazione. Se questa opzione è deselezionata (stato predefinito), quindi quando il Runtime di .NET compila il codice MSIL in codice della CPU, lascia le ottimizzazioni abilitate. Se l'opzione è selezionata, il debugger richiede che le ottimizzazioni disabilitato.

Per trovare le **disattivare l'ottimizzazione JIT al caricamento del modulo (solo gestito)** opzione, selezionare **Tools** > **opzioni**e quindi selezionare il  **Generali** pagina la **debug** nodo.

**Quando è necessario selezionare questa opzione:** Selezionare questa opzione quando si scaricano le DLL da un'altra origine, ad esempio un pacchetto nuget, e da sottoporre a debug il codice nella DLL. Affinché il corretto funzionamento, è anche necessario trovare il file di simboli (PDB) per questa DLL.

Se desidera utilizzare solo nel debug del codice che si compila in locale, è consigliabile lasciare questa opzione non è selezionata, come, in alcuni casi, l'abilitazione di questa opzione in modo significativo rallenterà il debug. Esistono due motivi per questo rallentamento:

* Codice ottimizzato viene eseguito più velocemente. Se consentono di disattivare le ottimizzazioni di grandi quantità di codice, l'impatto sulle prestazioni può sommare.
* Se si dispone di Just My Code abilitato, il debugger non lo è nemmeno tenta di caricare i simboli per DLL c / ottimizzati. Ricerca di simboli può richiedere molto tempo.

**Limitazioni di questa opzione:** Esistono due casi in cui questa opzione effettuerà **non** lavorare:

1. In situazioni in cui si collega il debugger a un processo già in esecuzione, questa opzione non avrà effetto sui moduli che sono stati già caricati al momento che è stato collegato il debugger.
2. Questa opzione non ha alcun effetto sulle DLL che sono stati precompilati (dette anche Ngen) al codice nativo. Tuttavia, è possibile disabilitare l'utilizzo di codice precompilato avviando il processo con l'ambiente di che variabili 'COMPlus_ZapDisable' impostato su '1'.

## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)
