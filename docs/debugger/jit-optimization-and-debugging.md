---
title: Ottimizzazione e debug JIT | Microsoft Docs
description: Il codice ottimizzato è più difficile da eseguire il debug rispetto al codice non. Informazioni sull'ottimizzazione JIT e su quando e come eliminarlo.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66f63c7232b52ebe849722147e007ab70527c311
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903922"
---
# <a name="jit-optimization-and-debugging"></a>Debug e ottimizzazione JIT
Se si sta provando a eseguire il debug del codice, è più facile quando il codice **non** è ottimizzato. Quando il codice viene ottimizzato, il compilatore e il runtime apportano modifiche al codice della CPU creato in modo che venga eseguito più velocemente, ma con un mapping meno diretto al codice sorgente originale. Se il mapping è meno diretto, spesso i debugger non sono in grado di indicare il valore delle variabili locali e l'esecuzione del codice e i punti di interruzione potrebbero non funzionare come previsto.

> [!NOTE]
> Per ulteriori informazioni sul debug JIT (just-in-Time), leggere [questa documentazione](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Funzionamento delle ottimizzazioni in .NET 
In genere, la configurazione della build di rilascio crea codice ottimizzato e la configurazione della build di debug non lo è. La `Optimize` Proprietà MSBuild controlla se il compilatore viene informato per ottimizzare il codice.

Nell'ecosistema .NET, il codice viene convertito dalle istruzioni di origine a CPU in un processo in due passaggi: innanzitutto, il compilatore C# converte il testo digitato in un formato binario intermedio denominato MSIL e scrive il codice MSIL in file con estensione dll. Successivamente, il Runtime .NET converte il codice MSIL in istruzioni per la CPU. Entrambi i passaggi possono essere ottimizzati a un certo livello, ma il secondo passaggio eseguito dal runtime .NET esegue le ottimizzazioni più significative.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Opzione ' non visualizzare l'ottimizzazione JIT al caricamento del modulo (solo gestito)'
Il debugger espone un'opzione che controlla cosa accade quando una DLL compilata con ottimizzazioni abilitate viene caricata all'interno del processo di destinazione. Se questa opzione è deselezionata (stato predefinito), quando il Runtime .NET compila il codice MSIL nel codice della CPU, lascia le ottimizzazioni abilitate. Se l'opzione è selezionata, il debugger richiede che le ottimizzazioni siano disabilitate.

Per trovare l'opzione **Disattiva l'ottimizzazione JIT al caricamento del modulo (solo gestito)** , selezionare **strumenti**  >  **Opzioni** e quindi selezionare la pagina **generale** nel nodo **debug** .

![Disattiva l'ottimizzazione JIT](../debugger/media/suppress-jit-tool-options.png "Disattiva l'ottimizzazione JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Quando è necessario selezionare l'opzione ' non visualizzare l'ottimizzazione JIT '?
Selezionare questa opzione quando si scaricano le dll da un'altra origine, ad esempio un pacchetto NuGet, e si vuole eseguire il debug del codice in questa DLL. Per il corretto funzionamento dell'eliminazione, è inoltre necessario trovare il file di simboli (con estensione pdb) per questa DLL.

Se si vuole solo eseguire il debug del codice che si sta compilando localmente, è preferibile lasciare deselezionata questa opzione, come, in alcuni casi, l'abilitazione di questa opzione rallenterà significativamente il debug. Questo rallentamento è dovuto a due motivi:

* Il codice ottimizzato viene eseguito più velocemente. Se si disattivano le ottimizzazioni per una grande quantità di codice, l'effetto sulle prestazioni può aumentare.
* Se Just My Code è abilitata, il debugger non tenterà neanche di caricare i simboli per le dll ottimizzate. La ricerca di simboli può richiedere molto tempo.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Limitazioni dell'opzione ' non visualizzare l'ottimizzazione JIT ' 
Ci sono due situazioni in cui l'attivazione di questa opzione **non** funziona:

1. Nei casi in cui si connette il debugger a un processo già in esecuzione, questa opzione non avrà alcun effetto sui moduli che erano già stati caricati nel momento in cui il debugger è stato collegato.
2. Questa opzione non ha alcun effetto sulle DLL precompilate (a. k. a ngen'ed) in codice nativo. Tuttavia, è possibile disabilitare l'utilizzo del codice precompilato avviando il processo con la variabile di ambiente **"COMPlus_ReadyToRun"** impostata su **"0"**. In questo modo si indica al runtime di .NET Core di disabilitare l'uso di immagini precompilate, forzando il runtime a compilare il codice del Framework. 

    > [!IMPORTANT]
    > Se la destinazione è .NET Framework o una versione precedente di .NET Core (2. x o inferiore), aggiungere anche la variabile di ambiente ' COMPlus_ZapDisable ' e impostarla su' 1'

    **Per impostare una variabile di ambiente per un progetto .NET Core in Visual Studio:**
    1. Nella **Esplora soluzioni** **fare clic con il pulsante destro del mouse** sul file di progetto e scegliere **proprietà**.
    2. Passare alla scheda **debug** e in **variabili di ambiente** fare clic sul pulsante **Aggiungi** .
    3. Impostare il nome (chiave) su **COMPlus_ReadyToRun** e impostare il valore su **0**.

    ![Imposta COMPlus_ReadyToRun variabile di ambiente](../debugger/media/environment-variables-debug-menu.png "Imposta COMPlus_ReadyToRun variabile di ambiente")

## <a name="see-also"></a>Vedere anche
- [Come eseguire il debug dell'origine DotNet Framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processo di esecuzione gestita](/dotnet/standard/managed-execution-process)
