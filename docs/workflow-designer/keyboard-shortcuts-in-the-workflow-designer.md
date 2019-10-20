---
title: 'Progettazione flussi di lavoro: tasti di scelta rapida'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36e8b6d67d2405fbc74c0b1bf854b3a3baaf4da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650149"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

È possibile accedere a tutte le funzionalità di base dell'Progettazione flussi di lavoro tramite tastiera.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigazione in Progettazione flussi di lavoro mediante la tastiera

All'interno di Visual Studio, i collegamenti globali e i collegamenti di debug si applicano al Progettazione flussi di lavoro. Sono stati creati anche alcuni tasti di scelta rapida Progettazione flussi di lavoro specifici. In Visual Studio è possibile rimappare tutti i tasti di scelta rapida. In un'applicazione riallocata, tuttavia, i tasti di scelta rapida sono hardcoded.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

Nella tabella seguente vengono riepilogati i tasti di scelta rapida predefiniti assegnati ai comandi Progettazione flussi di lavoro.

|Metodo rapido|Scopo|
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
|CTRL + ALT + F6|Sposta lo stato attivo dall'area dell'interfaccia utente corrente all'area successiva nella sequenza. L'ordine è il seguente:<br /><br /> 1. barra di spostamento.<br />2. area di progettazione<br />3. finestra di progettazione argomenti/variabili/importazioni se aperta<br />4. Shell|

### <a name="flowchart"></a>Diagramma di flusso

Nell'elenco seguente vengono presentate le operazioni necessarie per costruire un diagramma di flusso dalla tastiera. Come nel resto del Progettazione flussi di lavoro, le attività vengono aggiunte all'area di progettazione usando i collegamenti globali della casella degli strumenti forniti con Visual Studio.

- Per spostare un'attività, selezionarla e riposizionarla usando i tasti di direzione.

- Per ridimensionare un diagramma di flusso, spostare un'attività oltre il bordo corrente del diagramma di flusso usando i tasti di direzione. Il diagramma di flusso viene ridimensionato automaticamente.

- Per impostare un'attività come nodo iniziale, utilizzare il comando **Imposta come StartNode** nel menu di scelta rapida.

- Per connettere le attività:

    1. Selezionare l'attività di origine usando il tasto TAB.

    2. Premere CTRL+E, M il numero di volte necessario per spostare lo stato attivo sull'attività di destinazione.

    3. Premere CTRL+E, S per aggiungere l'attività di destinazione alla selezione.

    4. Premere CTRL+E, F per aggiungere il connettore dall'origine alla destinazione.

Note sulla connessione delle attività dalla tastiera:

- È possibile creare contemporaneamente più connessioni aggiungendo più attività alla selezione prima di premere CTRL+E, F. Le connessioni vengono create nell'ordine in cui le attività sono state aggiunte alla selezione.

- Se una coppia di attività non può essere connessa, ad esempio se per l'attività di origine è già presente una connessione in uscita, le altre connessioni tra le attività della selezione vengono comunque create quando possibile.

- Quando un **FlowDecision** viene incluso nella selezione e il **FlowDecision** non dispone di connettori in uscita, il connettore viene inserito nel ramo **true** .

### <a name="expression-editing"></a>Modifica dell'espressione

Per impostazione predefinita, i tasti di scelta rapida predefiniti per Visual Basic modifica del testo vengono applicati all'interno dell'editor espressioni in Progettazione flussi di lavoro, con le limitazioni seguenti:

- La modifica del mapping dei tasti di scelta rapida per i comandi seguenti non ha effetto. In caso di modifica di un'espressione, è possibile accedere a questi comandi solo mediante i tasti di scelta rapida predefiniti.

  - Taglia
  - Copia
  - Incolla
  - Seleziona tutto
  - Annulla
  - Ripristina

- Per modificare il mapping dei tasti di scelta rapida per i comandi di modifica delle espressioni all'interno Progettazione flussi di lavoro in Visual Studio, modificare i collegamenti nell'ambito del Progettazione flussi di lavoro. Le modifiche apportate nell'ambito dell'editor di testo non vengono applicate automaticamente ai Progettazione flussi di lavoro. Se si desidera modificare il mapping dei collegamenti in entrambi gli ambiti, è necessario applicare le modifiche due volte, una volta per ogni ambito.
