---
title: 'Progettazione flussi di lavoro: Tasti di scelta rapida'
description: Informazioni sui vari comandi che è possibile digitare sulla tastiera per spostarsi tra le Progettazione flussi di lavoro in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 4dcf52de12d2c6401a7715f36ad80ecfd6ed9f4f
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963645"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

Tutte le funzionalità principali del Progettazione flussi di lavoro sono accessibili tramite tastiera.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigazione in Progettazione flussi di lavoro mediante la tastiera

All'Visual Studio, i tasti di scelta rapida globali e i tasti di scelta rapida di debug si applicano al Progettazione flussi di lavoro. Inoltre, sono stati creati Progettazione flussi di lavoro tasti di scelta rapida specifici. In Visual Studio è possibile modificare il mapping di tutti i tasti di scelta rapida. In un'applicazione riallocata, tuttavia, i tasti di scelta rapida sono hardcoded.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tasti di scelta rapida di Progettazione flussi di lavoro

La tabella seguente riepiloga i tasti di scelta rapida predefiniti assegnati Progettazione flussi di lavoro comandi.

|Tasto di scelta rapida|Scopo|
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
|CTRL + ALT + F6|Sposta lo stato attivo dall'area dell'interfaccia utente corrente all'area successiva nella sequenza. L'ordine è il seguente:<br /><br /> 1. Barra di navigazione.<br />2. Area di progettazione<br />3. Finestra di progettazione Argomenti/Variabili/Importazioni se aperta<br />4. Shell|

### <a name="flowchart"></a>Diagramma di flusso

Nell'elenco seguente vengono presentate le operazioni necessarie per costruire un diagramma di flusso dalla tastiera. Come nel resto della finestra di Progettazione flussi di lavoro, le attività vengono aggiunte all'area di progettazione usando i tasti di scelta rapida globali della casella degli strumenti forniti con Visual Studio.

- Per spostare un'attività, selezionarla e riposizionarla usando i tasti di direzione.

- Per ridimensionare un diagramma di flusso, spostare un'attività oltre il bordo corrente del diagramma di flusso usando i tasti di direzione. Il diagramma di flusso viene ridimensionato automaticamente.

- Per impostare un'attività come nodo di avvio, usare il comando Imposta come **StartNode** nel menu di scelta rapida.

- Per connettere le attività:

    1. Selezionare l'attività di origine usando il tasto TAB.

    2. Premere CTRL+E, M il numero di volte necessario per spostare lo stato attivo sull'attività di destinazione.

    3. Premere CTRL+E, S per aggiungere l'attività di destinazione alla selezione.

    4. Premere CTRL+E, F per aggiungere il connettore dall'origine alla destinazione.

Note sulla connessione delle attività dalla tastiera:

- È possibile creare contemporaneamente più connessioni aggiungendo più attività alla selezione prima di premere CTRL+E, F. Le connessioni vengono create nell'ordine in cui le attività sono state aggiunte alla selezione.

- Se una coppia di attività non può essere connessa, ad esempio se per l'attività di origine è già presente una connessione in uscita, le altre connessioni tra le attività della selezione vengono comunque create quando possibile.

- Quando **flowDecision è** incluso nella selezione e **FlowDecision** non ha connettori in uscita, il connettore viene inserito nel **ramo True.**

### <a name="expression-editing"></a>Modifica dell'espressione

Per impostazione predefinita, i tasti di scelta rapida predefiniti Visual Basic modifica del testo vengono applicati all'interno dell'editor espressioni Progettazione flussi di lavoro, con le limitazioni seguenti:

- La modifica del mapping dei tasti di scelta rapida per i comandi seguenti non ha effetto. In caso di modifica di un'espressione, è possibile accedere a questi comandi solo mediante i tasti di scelta rapida predefiniti.

  - Taglia
  - Copia
  - Incolla
  - Seleziona tutto
  - Annulla
  - Ripeti

- Per modificare il mapping dei tasti di scelta rapida per i comandi di modifica delle espressioni all'interno Progettazione flussi di lavoro in Visual Studio, modificare i tasti di scelta rapida nell'Progettazione flussi di lavoro ambito. Le modifiche apportate nell'ambito dell'editor di testo non vengono applicate automaticamente Progettazione flussi di lavoro. Se si desidera modificare il mapping dei collegamenti in entrambi gli ambiti, è necessario applicare le modifiche due volte, una volta per ogni ambito.
