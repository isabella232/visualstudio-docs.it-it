---
title: Ottimizzazione e debug JIT | Microsoft Docs
description: Il debug del codice ottimizzato è più difficile rispetto al codice che non lo è. Informazioni sull'ottimizzazione JIT e su quando e come sopprimerla.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e6dae429c3083188fa9d7fbc37a48dda5a98b18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112594"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
Se si sta tentando di eseguire il debug del codice, è più semplice quando tale codice **NON è ottimizzato.** Quando il codice è ottimizzato, il compilatore e il runtime apportano modifiche al codice CPU generato in modo che venga eseguito più velocemente, ma abbia un mapping meno diretto al codice sorgente originale. Se il mapping è meno diretto, i debugger spesso non sono in grado di indicare il valore delle variabili locali e l'esecuzione di istruzioni del codice e i punti di interruzione potrebbero non funzionare come previsto.

> [!NOTE]
> Per altre informazioni sul debug JIT (Just-In-Time), leggere [questa documentazione.](../debugger/debug-using-the-just-in-time-debugger.md)

## <a name="how-optimizations-work-in-net"></a>Funzionamento delle ottimizzazioni in .NET 
In genere, la configurazione della build di rilascio crea codice ottimizzato e la configurazione della build debug no. La `Optimize` MSBuild controlla se al compilatore viene detto di ottimizzare il codice.

Nell'ecosistema .NET il codice viene trasformato da istruzioni di origine a CPU in un processo in due passaggi: in primo luogo, il compilatore C# converte il testo digitato in un formato binario intermedio denominato MSIL e scrive il codice MSIL in .dll file. Successivamente, il runtime .NET converte questo codice MSIL in istruzioni della CPU. Entrambi i passaggi possono essere ottimizzati in qualche modo, ma il secondo passaggio eseguito dal runtime .NET esegue le ottimizzazioni più significative.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Opzione "Elimina ottimizzazione JIT al caricamento del modulo (solo gestito)"
Il debugger espone un'opzione che controlla cosa accade quando una DLL compilata con ottimizzazioni abilitate viene caricata all'interno del processo di destinazione. Se questa opzione è deselezionata (lo stato predefinito), quando il runtime .NET compila il codice MSIL nel codice CPU, lascia abilitate le ottimizzazioni. Se l'opzione è selezionata, il debugger richiede che le ottimizzazioni siano disabilitate.

Per trovare l'opzione Elimina ottimizzazione JIT al caricamento del modulo **(solo gestito),** selezionare Opzioni strumenti e quindi selezionare la pagina Generale  >  nel **nodo** Debug. 

![Eliminazione dell'ottimizzazione JIT](../debugger/media/suppress-jit-tool-options.png "Eliminazione dell'ottimizzazione JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Quando è necessario selezionare l'opzione "Elimina ottimizzazione JIT"?
Selezionare questa opzione quando si scaricano le DLL da un'altra origine, ad esempio un pacchetto nuget, e si vuole eseguire il debug del codice in questa DLL. Per il funzionamento dell'eliminazione, è necessario trovare anche il file di simboli (con estensione pdb) per questa DLL.

Se si è interessati solo al debug del codice che si sta compilando in locale, è meglio lasciare deselezionata questa opzione, in quanto, in alcuni casi, l'abilitazione di questa opzione rallenta significativamente il debug. Questo rallentamento può essere rallentato per due motivi:

* Il codice ottimizzato viene eseguito più velocemente. Se si disattivano le ottimizzazioni per una grande quantità di codice, l'impatto sulle prestazioni può essere sommato.
* Se l'Just My Code abilitata, il debugger non tenterà neanche di caricare i simboli per le DLL ottimizzate. La ricerca di simboli può richiedere molto tempo.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Limitazioni dell'opzione "Elimina ottimizzazione JIT" 
Esistono due situazioni in cui l'attivazione di questa opzione **NON funziona:**

1. Nelle situazioni in cui si collega il debugger a un processo già in esecuzione, questa opzione non avrà alcun effetto sui moduli già caricati al momento della connessione del debugger.
2. Questa opzione non ha alcun effetto sulle DLL precompilato (ovvero ngen'ed) nel codice nativo. È tuttavia possibile disabilitare l'utilizzo del codice precompilato avviando il processo con la variabile di ambiente **"COMPlus_ReadyToRun"** impostata su **"0".** In questo modo il runtime di .NET Core disabilita l'uso di immagini precompilato, forzando il runtime al codice del framework di compilazione JIT. 

    > [!IMPORTANT]
    > Se si ha come destinazione .NET Framework o una versione precedente di .NET Core (2.x o versione successiva), aggiungere anche la variabile di ambiente "COMPlus_ZapDisable" e impostarla su "1"

    **Per impostare una variabile di ambiente per un progetto .NET Core in Visual Studio:**
    1. Nella finestra **Esplora soluzioni** fare clic **con il pulsante destro** del mouse sul file di progetto e scegliere **Proprietà**.
    2. Passare alla scheda **Debug** e in **Variabili di ambiente** fare clic sul **pulsante** Aggiungi.
    3. Impostare Name (Key) su **COMPlus_ReadyToRun** e Value su **0.**

    ![Impostare COMPlus_ReadyToRun di ambiente](../debugger/media/environment-variables-debug-menu.png "Impostare COMPlus_ReadyToRun di ambiente")

## <a name="see-also"></a>Vedi anche
- [Come eseguire il debug dell'origine dotnet framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)
