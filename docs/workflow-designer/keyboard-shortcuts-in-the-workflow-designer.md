---
title: Finestra di progettazione del flusso di lavoro - scelte rapide da tastiera nella finestra di progettazione del flusso di lavoro
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4040a5b370674e7794b09e4d1cae68f424c7792
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887371"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

Tutte le funzionalità principali della finestra di progettazione del flusso di lavoro è accessibile dalla tastiera.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigazione in Progettazione flussi di lavoro mediante la tastiera

All'interno di Visual Studio, i collegamenti globali e collegamenti di debug si applicano alla finestra di progettazione del flusso di lavoro. Inoltre, un numero di scelte rapide da tastiera specifiche di progettazione del flusso di lavoro è stato creato. In Visual Studio, tutti i tasti di scelta rapida possono essere rimappati. In un'applicazione riallocata, tuttavia, i tasti di scelta rapida sono hardcoded.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

Nella tabella seguente sono riepilogati i tasti di scelta assegnati ai comandi di progettazione del flusso di lavoro.

|Collegamento|Scopo|
|-|-------------|
|CTRL+E, A|Mostra o nasconde Progettazione argomenti.|
|CTRL+E, C|Comprime l'attività selezionata sul posto.|
|CTRL+E, E|Espande l'attività selezionata sul posto.|
|CTRL+E, F|Connette le attività selezionate in un diagramma di flusso.|
|CTRL+E, I|Mostra o nasconde la finestra di progettazione importazioni.|
|CTRL+E, M|Sposta lo stato attivo sull'elemento successivo nell'ordine di tabulazione.|
|CTRL+E, N|Crea una nuova variabile nell'ambito dell'attività selezionata (o quella più vicina).|
|CTRL+E, O|Mostra o nasconde la carta panoramica.|
|CTRL+E, P|Consente di passare all'attività padre dell'attività selezionata. Consente di salire di un livello nell'esplorazione tramite la barra di navigazione e di modificare l'attività radice nell'area di progettazione.|
|CTRL+E, S|Aggiunge alla selezione corrente l'elemento con stato attivo.|
|CTRL+E, V|Mostra o nasconde Progettazione variabili.|
|CTRL+E, X|Espande tutte le attività nel flusso di lavoro.|
|CTRL + ALT + F6|Sposta lo stato attivo dall'area dell'interfaccia utente corrente all'area successiva nella sequenza. L'ordine è il seguente:<br /><br /> 1.  Barra di navigazione.<br />2.  Area di progettazione<br />3.  Argomenti/Variabili/finestra di progettazione importazioni, se aperta<br />4.  Shell|

### <a name="flowchart"></a>Diagramma di flusso

Nell'elenco seguente vengono presentate le operazioni necessarie per costruire un diagramma di flusso dalla tastiera. Come nella parte rimanente della finestra di progettazione del flusso di lavoro, le attività vengono aggiunte all'area di progettazione usando i tasti di scelta rapida globale della casella degli strumenti forniti con Visual Studio.

- Per spostare un'attività, selezionarla e riposizionarla usando i tasti di direzione.

- Per ridimensionare un diagramma di flusso, spostare un'attività oltre il bordo corrente del diagramma di flusso usando i tasti di direzione. Il diagramma di flusso viene ridimensionato automaticamente.

- Per impostare un'attività come nodo iniziale, usare il **imposta come StartNode** comando nel menu di scelta rapida.

- Per connettere le attività:

    1.  Selezionare l'attività di origine usando il tasto TAB.

    2.  Premere CTRL+E, M il numero di volte necessario per spostare lo stato attivo sull'attività di destinazione.

    3.  Premere CTRL+E, S per aggiungere l'attività di destinazione alla selezione.

    4.  Premere CTRL+E, F per aggiungere il connettore dall'origine alla destinazione.

Note sulla connessione delle attività dalla tastiera:

- È possibile creare contemporaneamente più connessioni aggiungendo più attività alla selezione prima di premere CTRL+E, F. Le connessioni vengono create nell'ordine in cui le attività sono state aggiunte alla selezione.

- Se una coppia di attività non può essere connessa, ad esempio se per l'attività di origine è già presente una connessione in uscita, le altre connessioni tra le attività della selezione vengono comunque create quando possibile.

- Quando un **FlowDecision** è incluso nella selezione e il **FlowDecision** non dispone di alcun connettori in uscita, il connettore viene posizionato sul **True** ramo.

### <a name="expression-editing"></a>Modifica dell'espressione

Per impostazione predefinita, i tasti predefinite per la modifica del testo di Visual Basic si applicano nell'editor di espressioni nella finestra di progettazione del flusso di lavoro con le limitazioni seguenti:

- La modifica del mapping dei tasti di scelta rapida per i comandi seguenti non ha effetto. In caso di modifica di un'espressione, è possibile accedere a questi comandi solo mediante i tasti di scelta rapida predefiniti.

   - Taglia
   - Copia
   - Incolla
   - Seleziona tutto
   - Annulla
   - Ripristina

- Per rimappare i tasti di scelta rapida per i comandi di modifica espressione all'interno di progettazione del flusso di lavoro in Visual Studio, modificare i collegamenti nell'ambito di progettazione del flusso di lavoro. Le modifiche apportate nell'Editor di testo ambito non si applicano automaticamente alla finestra di progettazione del flusso di lavoro. Se si desidera modificare il mapping dei collegamenti in entrambi gli ambiti, è necessario applicare le modifiche due volte, una volta per ogni ambito.