---
title: Ottimizzazione e debug JIT | Microsoft Docs
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
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731627"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
**Funzionamento delle ottimizzazioni in .NET:** Se si sta provando a eseguire il debug del codice, è più facile quando il codice **non** è ottimizzato. Questo è dovuto al fatto che quando il codice è ottimizzato, il compilatore e il runtime apportano modifiche al codice della CPU creato in modo che venga eseguito più velocemente, ma con un mapping meno diretto al codice sorgente originale. Ciò significa che i debugger spesso non riescono a indicare il valore delle variabili locali e l'esecuzione del codice e i punti di interruzione potrebbero non funzionare come previsto.

In genere, la configurazione della build di rilascio crea codice ottimizzato e la configurazione della build di debug non lo è. Il `Optimize` proprietà MSBuild controlla se il compilatore viene informato per ottimizzare il codice.

Nell'ecosistema .NET, il codice viene convertito dalle istruzioni di origine a CPU in un processo in due passaggi: innanzitutto C# , il compilatore converte il testo digitato in un formato binario intermedio denominato MSIL e lo scrive in file con estensione dll. Successivamente, il Runtime .NET converte il codice MSIL in istruzioni per la CPU. Entrambi i passaggi possono essere ottimizzati a un certo livello, ma il secondo passaggio eseguito dal runtime .NET esegue le ottimizzazioni più significative.

**Opzione ' non visualizzare l'ottimizzazione JIT al caricamento del modulo (solo gestito)':** Il debugger espone un'opzione che controlla cosa accade quando una DLL compilata con ottimizzazioni abilitate viene caricata all'interno del processo di destinazione. Se questa opzione è deselezionata (stato predefinito), quando il Runtime .NET compila il codice MSIL nel codice della CPU, lascia le ottimizzazioni abilitate. Se l'opzione è selezionata, il debugger richiede che le ottimizzazioni siano disabilitate.

Per trovare l' **opzione Disattiva ottimizzazione JIT al caricamento del modulo (solo gestito)** , selezionare **strumenti**  > **Opzioni**e quindi selezionare la pagina **generale** nel nodo **debug** .

**Quando è necessario selezionare questa opzione:** Selezionare questa opzione quando si scaricano le dll da un'altra origine, ad esempio un pacchetto NuGet, e si vuole eseguire il debug del codice in questa DLL. Per funzionare, è inoltre necessario trovare il file di simboli (con estensione pdb) per questa DLL.

Se si vuole solo eseguire il debug del codice che si sta compilando localmente, è preferibile lasciare deselezionata questa opzione, come, in alcuni casi, l'abilitazione di questa opzione rallenterà significativamente il debug. Questo rallentamento è dovuto a due motivi:

* Il codice ottimizzato viene eseguito più velocemente. Se si disattivano le ottimizzazioni per una grande quantità di codice, l'effetto sulle prestazioni può aumentare.
* Se Just My Code è abilitata, il debugger non tenterà neanche di caricare i simboli per le dll ottimizzate. La ricerca di simboli può richiedere molto tempo.

**Limitazioni di questa opzione:** Esistono due situazioni in cui questa opzione **non** funzionerà:

1. Nei casi in cui si connette il debugger a un processo già in esecuzione, questa opzione non avrà alcun effetto sui moduli che erano già stati caricati nel momento in cui il debugger è stato collegato.
2. Questa opzione non ha alcun effetto sulle DLL precompilate (a. k. a ngen'ed) in codice nativo. Tuttavia, è possibile disabilitare l'utilizzo del codice precompilato avviando il processo con la variabile di ambiente ' COMPlus_ZapDisable ' impostata su' 1'.

## <a name="see-also"></a>Vedere anche
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
- [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)
