---
title: Eseguire il debug di codice ottimizzato | Microsoft Docs
description: Se possibile, non compilare una destinazione della versione Win32 fino a quando non viene eseguito il debug del programma, perché l'ottimizzazione può complicare il debug. Vedere i dettagli in questo articolo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3d58233f606c3060a1a78f8cfd0a1c3b4c0334de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128599"
---
# <a name="how-to-debug-optimized-code"></a>Procedura: eseguire il debug di codice ottimizzato

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> L'opzione del compilatore [/Zo (Ottimizzare il debug)](/cpp/build/reference/zo-enhance-optimized-debugging) (introdotta in Visual Studio Update 3) genera informazioni più complete sul debug per il codice ottimizzato (progetti non compilati con l'opzione del compilatore **/Od**). Vedere [Opzioni /O (Ottimizza codice)](/cpp/build/reference/o-options-optimize-code). Questo include un supporto migliorato per il debug delle variabili locali e delle funzioni inline.
>
> [Modifica e continuazione](../debugger/edit-and-continue-visual-csharp.md) è disabilitato quando viene usata l'opzione del compilatore **/Zo**.

 Quando il compilatore ottimizza il codice, modifica la posizione e l'organizzazione delle istruzioni. IL risultato è un codice compilato più efficace. A causa di questa ridisposizione, il debugger non è sempre in grado di identificare il codice sorgente corrispondente a un set di istruzioni.

 L'ottimizzazione del codice può influenzare:

- Le variabili locali, che possono essere rimosse o spostate in posizioni non riconosciute dal debugger

- Le posizioni all'interno di una funzione, che vengono modificate quando l'utilità di ottimizzazione esegue l'unione di blocchi di codice.

- I nomi delle funzioni per i frame nello stack di chiamate, che potrebbero risultare errati se due funzioni vengono unite.

  I frame visualizzati nello stack di chiamate sono in genere corretti, se si dispone di simboli per ciascuno di essi. I frame nello stack di chiamate risulteranno errati se lo stack è danneggiato, se sono presenti funzioni scritte in linguaggio assembly oppure se esistono frame del sistema operativo privi di simboli corrispondenti nello stack di chiamate.

  Le variabili globali e di tipo statico vengono visualizzate sempre correttamente, analogamente al layout delle strutture. Se si dispone di un puntatore a una struttura e il valore di questo puntatore è corretto, tutte le variabili membro della struttura conterranno il valore corretto.

  A causa di queste limitazioni, è opportuno eseguire il debug usando, se possibile, una versione del programma non ottimizzata. Per impostazione predefinita, l'ottimizzazione è disattivata nella configurazione debug di un programma C++ e attivata nella configurazione versione.

  Può tuttavia accadere che un bug venga individuato solo nella versione ottimizzata di un programma. In tal caso è necessario effettuare il debug del codice ottimizzato.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Per attivare l'ottimizzazione nella configurazione di una build di debug

1. Quando si crea un nuovo progetto, selezionare la destinazione `Win32 Debug`. Usare la destinazione `Win32 Debug` finché non viene completato il debug del programma e non si è pronti a compilare una destinazione `Win32 Release`. Il compilatore non ottimizza la destinazione `Win32 Debug`.

2. Selezionare il progetto in Esplora soluzioni.

3. Nel menu **Visualizza** fare clic su **Pagine delle proprietà**.

4. Nella finestra di dialogo **Pagine delle proprietà** verificare che sia selezionata la voce `Debug` nell'elenco a discesa **Configurazione**.

5. Nella struttura di cartelle visualizzata a sinistra selezionare la cartella **C/C++**.

6. Nella cartella **C++** selezionare `Optimization`.

7. Nell'elenco di proprietà situato a destra cercare `Optimization`. L'impostazione accanto probabilmente indica `Disabled (` [/Od](/cpp/build/reference/od-disable-debug) `)` . Scegliere una delle altre opzioni ( `Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization)o `)` `Custom` ).

8. Se si è scelto l'opzione `Custom` per `Optimization`, a questo punto è possibile impostare le opzioni per le altre proprietà presenti nell'elenco.

9. Selezionare il nodo Proprietà di configurazione, C/C++, Riga di comando della pagina delle proprietà del progetto e aggiungere `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` alla casella **di** testo Opzioni aggiuntive.

    > [!WARNING]
    > `/Zo` richiede Visual Studio 2013 Update 3 o una versione successiva.
    >
    >  L'aggiunta di `/Zo` disabilita [Modifica e continuazione](../debugger/edit-and-continue-visual-csharp.md).

   Quando si esegue il debug di codice ottimizzato, controllare nella finestra **Disassembly** quali istruzioni vengono effettivamente create ed eseguite. Nell'impostazione di punti di interruzione, è necessario sapere che un punto di interruzione può essere spostato insieme a un'istruzione. Si consideri il codice di esempio seguente:

```cpp
for (x=0; x<10; x++)
```

 Si supponga di impostare un punto di interruzione in questa riga. Ci si aspetterebbe che il punto di interruzione venga raggiunto 10 volte, ma se il codice è ottimizzato, il punto di interruzione verrà raggiunto solo una volta. Ciò è dovuto al fatto che la prima istruzione imposta il valore di `x` su 0. Il compilatore riconosce che questa operazione deve essere eseguita solo una volta ed esce dal ciclo. Il punto di interruzione si sposta con essa. Le istruzioni che confrontano e incrementano `x` rimangono all'interno del ciclo. Quando si visualizza la finestra **Disassembly**, l'[unità di esecuzione](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) viene impostata automaticamente su Istruzione per consentire un maggiore controllo, utile se si esegue il codice un'istruzione alla volta.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)