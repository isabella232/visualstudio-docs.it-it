---
title: Scelte rapide da tastiera e mouse per Progettazione classi
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30932a6c94bc6104aeea0244f06f471d0a639b21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533666"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe

È possibile usare la tastiera oltre al mouse per eseguire operazioni di spostamento in **Progettazione classi** e nella finestra **Dettagli classe**.

## <a name="use-the-mouse-in-class-designer"></a>Uso del mouse in Progettazione classi

Nei diagrammi classi sono supportate le operazioni del mouse seguenti:

|Combinazione del mouse|Context|Descrizione|
| - |-------------|-----------------|
|Doppio clic|Elementi forma|Apre l'editor del codice.|
|Doppio clic|Connettore simbolo|Espande/comprime il simbolo.|
|Doppio clic|Etichetta del connettore simbolo|Richiama il comando **Mostra interfaccia**.|
|Rotellina del mouse|Diagramma classi|Scorre verticalmente.|
|**MAIUSC** + rotellina del mouse|Diagramma classi|Scorre orizzontalmente.|
|**CTRL** + rotellina del mouse|Diagramma classi|Ingrandisce.|
|**CTRL** + **MAIUSC** + clic|Diagramma classi|Ingrandisce.|

## <a name="use-the-mouse-in-the-class-details-window"></a>Uso del mouse nella finestra Dettagli classe

Utilizzando un mouse, è possibile modificare l'aspetto della finestra **Dettagli classe** e i dati visualizzati nei modi seguenti:

- Facendo clic in qualsiasi cella modificabile è possibile modificarne il contenuto. Tutte le modifiche apportate si riflettono in tutte le posizioni in cui i dati sono archiviati o visualizzati, anche nella finestra **Proprietà** e nel codice sorgente.

- Se si fa clic in una cella di una riga, nella finestra **Proprietà** vengono visualizzate le proprietà relative all'elemento rappresentato da tale riga.

- Per cambiare la larghezza di una colonna, trascinare il bordo sul lato destro dell'intestazione della colonna fino a ottenere la larghezza desiderata.

- Per espandere o comprimere nodi di raggruppamenti o proprietà, fare clic sui simboli freccia a sinistra della riga.

- La finestra **Dettagli classe** contiene diversi pulsanti che consentono di creare nuovi membri nella classe corrente e di spostarsi tra i raggruppamenti dei membri nella griglia della **finestra**.

## <a name="use-the-keyboard-in-class-designer"></a>Uso della tastiera in Progettazione classi

Nei diagrammi classi sono supportate le operazioni della tastiera seguenti:

|Chiave|Context|Descrizione|
|---------|-------------|-----------------|
|**Tasti di direzione**|All'interno delle forme dei tipi|Navigazione nel contenuto della forma in un formato struttura ad albero (è supportato il wrapping per la forma). I tasti freccia sinistra e destra espandono/comprimono l'elemento corrente se è espandibile; in caso contrario permettono di passare all'elemento padre (vedere le informazioni sulla navigazione nella visualizzazione struttura ad albero per i informazioni dettagliate sul comportamento).|
|**Tasti di direzione**|Forme di primo livello|Consentono di spostare forme nel diagramma.|
|**Sposta** + **tasti** di direzione|All'interno delle forme dei tipi|Creazione della selezione continua costituita da elementi della forma quali membri, tipi nidificati o raggruppamenti. Questi tasti di scelta rapida non supportano il wrapping.|
|**Home**|All'interno delle forme dei tipi|Passa al titolo della forma di primo livello.|
|**Home**|Forme di primo livello|Passa alla prima forma del diagramma.|
|**Fine**|All'interno delle forme dei tipi|Passa all'ultimo elemento visibile all'interno della forma.|
|**Fine**|Forme di primo livello|Passa all'ultima forma del diagramma.|
|**Sposta** + **Pagina iniziale**|All'interno della forma del tipo|Seleziona gli elementi all'interno della forma a partire dall'elemento corrente e fino a quello in primo piano sulla stessa forma.|
|**Sposta** + **Fine**|All'interno della forma del tipo|Uguale a **MAIUSC** + **Home** ma nella direzione dall'alto verso il basso.|
|**Entrare**|Tutti i contesti|Richiama l'operazione predefinita sulla forma, che è disponibile anche tramite doppio clic. Nella maggior parte dei casi si tratta di Visualizza codice, ma per alcuni elementi la definizione è differente (simboli, intestazioni di raggruppamenti, etichette di simboli).|
|**+** e **-**|Tutti i contesti|Se l'elemento con lo stato attivo è espandibile, questi tasti espandono o comprimono l'elemento.|
|**>**|Tutti i contesti|Per gli elementi con elementi figlio, espande l'elemento se è compresso e passa al primo figlio.|
|**<**|Tutti i contesti|Passa all'elemento padre.|
|**ALT** + **Sposta** + **L**|All'interno delle forme dei tipi + sulle forme dei tipi|Passa al simbolo della forma selezionata, se presente.|
|**ALT** + **Sposta** + **B**|All'interno delle forme dei tipi + sulle forme dei tipi|Se l'elenco di tipi di base è visualizzato sulla forma del tipo e contiene più di un elemento, comprime o espande l'elenco.|
|**Elimina**|Sulle forme dei tipi e le forme Commenti|Richiama il comando **Rimuovi dal diagramma**.|
|**Elimina**|Su tutti gli altri elementi.|Richiama il comando **Delete from Code** (Elimina dal codice) (membri, parametri, associazioni, ereditarietà, etichette di simboli).|
|**CTRL** + **Elimina**|Tutti i contesti|Richiama il comando **Delete from Code** (Elimina dal codice) sulla selezione.|
|**Scheda**|Tutti i contesti|Passa all'elemento figlio successivo all'interno dello stesso elemento padre (supporta il wrapping).|
|**Sposta** + **Scheda**|Tutti i contesti|Passa all'elemento figlio precedente all'interno dello stesso elemento padre (supporta il wrapping).|
|**BARRA SPAZIATRICE**|Tutti i contesti|Alterna la selezione sull'elemento corrente.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Uso della tastiera nella finestra Dettagli classe

> [!NOTE]
> Le seguenti combinazioni di tasti sono state scelte specificamente per riprodurre l'operazione di digitazione di codice.

Per spostarsi nella finestra **Dettagli classe**, usare i seguenti tasti:

|Chiave|Risultato|
|-|-|
|**,** (virgola)|Se il cursore è posizionato in una riga di parametri, viene spostato nel campo Nome del parametro successivo. Se il cursore si trova nell'ultima riga di parametri di un metodo, il cursore viene spostato nel \<add parameter> campo, che può essere usato per creare un nuovo parametro.<br /><br /> Se il cursore è posizionato in un altro punto della finestra **Dettagli classe**, viene effettivamente aggiunta una virgola nel campo corrente.|
|**;** (punto e virgola) o **)** (parentesi di chiusura)|Sposta il cursore nel campo Nome della riga di membri successiva nella griglia della finestra **Dettagli classe**.|
|**Scheda**|Sposta il cursore nel campo successivo, prima da sinistra a destra e poi dall'alto verso il basso. Se il cursore viene spostato da un campo in cui è stato digitato del testo, in **Dettagli classe** il testo viene elaborato e memorizzato se non genera un errore.<br /><br /> Se il cursore si trova in un campo vuoto, ad esempio \<add parameter> , TAB lo sposta nel primo campo della riga successiva.|
|**BARRA SPAZIATRICE**|Sposta il cursore nel campo successivo, prima da sinistra a destra e poi dall'alto verso il basso. Se il cursore si trova in un campo vuoto, ad esempio \<add parameter> , viene spostato nel primo campo della riga successiva. Si noti che \<space> digitato immediatamente dopo la virgola viene ignorato.<br /><br /> Se il cursore si trova nel campo Riepilogo, viene aggiunto uno spazio.<br /><br /> Se il cursore si trova nella colonna Nascondi di una determinata riga, il valore della casella di controllo Nascondi viene attivato/disattivato.|
|**CTRL** + **Scheda**|Passa a un'altra finestra del documento, ad esempio dalla finestra **Dettagli classe** a un file di codice aperto.|
|**ESC**|Se è stata iniziata la digitazione di testo in un campo, il tasto ESC agisce da tasto di annullamento, ripristinando il valore precedente del contenuto del campo. Se la finestra Dettagli classe ha lo stato attivo generale, ma nessuna cella specifica è attiva, il tasto ESC sposta lo stato attivo dalla finestra **Dettagli classe**.|
|Freccia **su** e freccia **giù**|Questi tasti spostano il cursore da riga a riga verticalmente nella griglia della finestra **Dettagli classe**.|
|**Freccia sinistra**|Se il cursore si trova nella colonna Nome, comprime il nodo corrente della gerarchia (se aperto).|
|**Freccia destra**|Se il cursore si trova nella colonna Nome, espande il nodo corrente della gerarchia (se compresso).|

## <a name="see-also"></a>Vedere anche

- [Creare e configurare membri dei tipi](creating-and-configuring-type-members.md)
- [Come usare esclusivamente la tastiera](../reference/how-to-use-the-keyboard-exclusively.md)
- [Tasti di scelta rapida predefiniti in Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Tasti di scelta rapida in Blend](../../xaml-tools/keyboard-shortcuts-in-blend.md)
