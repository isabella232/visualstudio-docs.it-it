---
title: Visualizzare i valori delle variabili nei suggerimenti dati | Microsoft Docs
description: Usare i suggerimenti dati per visualizzare comodamente le informazioni sulle variabili, incluse le matrici e le strutture, durante il debug. È anche possibile modificare i valori.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5c9d0449fca38371e07ddaca6cef8758f53a2aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904921"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Visualizzare i valori dei dati nei suggerimenti dati nell'editor di codice

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente. Se è la prima volta che si tenta di eseguire il debug del codice, è consigliabile leggere il [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

## <a name="work-with-datatips"></a>Usare i suggerimenti dati

I suggerimenti dati vengono visualizzati solo in modalità di interruzioni e solo in variabili che si trovano nell'ambito corrente di esecuzione.

### <a name="display-a-datatip"></a>Visualizzare un DataTip

1. Impostare un punto di interruzione nel codice e avviare il debug premendo **F5** o selezionando **debug**  >  **Avvia debug**.

1. Quando viene sospesa in corrispondenza del punto di interruzione, passare il mouse su qualsiasi variabile nell'ambito corrente. Viene visualizzato un DataTip che mostra il nome e il valore corrente della variabile.

### <a name="make-a-datatip-transparent"></a>Rendere trasparente un DataTip

Per rendere trasparente un DataTip per visualizzare il codice sottostante, mentre si trova in DataTip, premere **CTRL**. Il DataTip rimane trasparente finché si tiene premuto il tasto **CTRL** . Questa operazione non funziona per i suggerimenti dati bloccati o mobili.
### <a name="pin-a-datatip"></a>Aggiungere un DataTip

Per aggiungere un DataTip in modo che rimanga aperto, selezionare l'icona **a puntina da disegno pin a origine** .

![Aggiungere un DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "Aggiungere un DataTip")

È possibile spostare un DataTip aggiunto trascinandolo intorno alla finestra del codice. Viene visualizzata un'icona a puntina da disegno sulla barra accanto alla riga a cui è stato aggiunto il DataTip.

>[!NOTE]
>I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nella posizione corrente del cursore o del DataTip. Se si passa il mouse su una variabile in un'altra funzione con lo stesso nome di una variabile nel contesto corrente, viene visualizzato il valore della variabile nel contesto corrente.

### <a name="unpin-a-datatip-from-source"></a>Rimuovi un DataTip dall'origine

Per rendere mobile un DataTip aggiunto, passare il puntatore del mouse su DataTip e selezionare l'icona della puntina da disegno dal menu di scelta rapida.

L'icona a forma di puntina da disegno passa alla posizione sbloccata e il DataTip ora è float o può essere trascinato sopra tutte le finestre aperte. I suggerimenti dati mobili si chiudono al termine della sessione di debug.

### <a name="repin-a-datatip"></a>Repin a DataTip

Per impostare un DataTip mobile su Source, passare il puntatore del mouse su di esso nell'editor di codice e selezionare l'icona della puntina da disegno. L'icona a forma di puntina da disegno passa alla posizione bloccata e DataTip viene nuovamente aggiunto solo alla finestra del codice.

Se un DataTip è mobile su una finestra del codice non sorgente, l'icona della puntina da disegno non è disponibile e non è possibile riaggiungere DataTip. Per accedere all'icona a puntina da disegno, restituire DataTip alla finestra dell'editor del codice trascinandolo o assegnando lo stato attivo alla finestra del codice.

### <a name="close-a-datatip"></a>Chiudere un DataTip

Per chiudere un DataTip, passare il puntatore del mouse su DataTip e selezionare l'icona Chiudi (**x**) dal menu di scelta rapida.

### <a name="close-all-datatips"></a>Chiudi tutti i suggerimenti dati

Per chiudere tutti i suggerimenti dati, scegliere **Cancella tutti i suggerimenti** dati dal menu **debug** .

### <a name="close-all-datatips-for-a-specific-file"></a>Chiudi tutti i suggerimenti dati per un file specifico

Per chiudere tutti i suggerimenti dati per un file specifico, scegliere **Cancella tutti i suggerimenti dati \<Filename> aggiunti a** dal menu **debug** .

## <a name="expand-and-edit-information"></a>Espandi e modifica informazioni
È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.

### <a name="expand-a-variable"></a>Espandi una variabile

Per espandere un oggetto in un DataTip per visualizzarne gli elementi, posizionare il puntatore del mouse sulle frecce di espansione prima dei nomi degli elementi per visualizzare gli elementi nel form albero. Per un DataTip aggiunto, selezionare il **+** prima del nome della variabile, quindi espandere l'albero.

![Espandi un DataTip](../debugger/media/dbg-tour-data-tips.png "Espandi un DataTip")

È possibile utilizzare il mouse o i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso nella visualizzazione espansa.

È anche possibile aggiungere elementi espansi al DataTip aggiunto passando il mouse su di essi e selezionando le relative icone a puntina da disegno. Gli elementi vengono quindi visualizzati nel DataTip aggiunto dopo che l'albero è stato compresso.

### <a name="edit-the-value-of-a-variable"></a>Modificare il valore di una variabile

Per modificare il valore di una variabile o di un elemento in un DataTip, selezionare il valore, digitare un nuovo valore e premere **invio**. La selezione è disabilitata per i valori di sola lettura.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Aggiungere proprietà nei suggerimenti dati

> [!NOTE]
> Questa funzionalità è supportata per .NET Core 3,0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle rispettive proprietà nei suggerimenti dati con lo strumento **Proprietà aggiungibili** .  Per usare questo strumento, passare il puntatore del mouse su una proprietà e selezionare l'icona a forma di puntina visualizzata oppure fare clic con il pulsante destro del mouse e selezionare l'opzione **Aggiungi membro come preferito** nel menu di scelta rapida risultante.  Questa operazione consente di eseguire il bubbling della proprietà nella parte superiore dell'elenco di proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella colonna a destra di DataTip.  Per Rimuovi una proprietà, selezionare di nuovo l'icona del PIN oppure selezionare il **membro Rimuovi come opzione preferita** nel menu di scelta rapida.

![Aggiunta di una proprietà in un DataTip](../debugger/media/basic-pin-datatip.gif "Aggiunta di una proprietà in un DataTip")

È anche possibile impostare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto in un DataTip.  È possibile accedere a una delle due opzioni facendo clic con il pulsante destro del mouse su una riga contenente una proprietà e selezionando la voce **Mostra solo membri aggiunti** o **Nascondi nomi membri bloccati nelle opzioni dei valori** del menu di scelta rapida.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualizzare tipi di dati complessi

Un'icona a forma di lente di ingrandimento accanto a una variabile o a un elemento in un DataTip significa che uno o più [visualizzatori](../debugger/create-custom-visualizers-of-data.md), ad esempio il [Visualizzatore di testo](../debugger/string-visualizer-dialog-box.md), sono disponibili per la variabile. I visualizzatori visualizzano le informazioni in modo più significativo e talvolta grafico.

Per visualizzare l'elemento usando il visualizzatore predefinito per il tipo di dati, selezionare l' ![icona del Visualizzatore](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore")icona a forma di lente di ingrandimento. Selezionare la freccia accanto all'icona a forma di lente di ingrandimento per selezionare da un elenco di visualizzatori per il tipo di dati.

## <a name="add-a-variable-to-a-watch-window"></a>Aggiungere una variabile a un finestra Espressioni di controllo

Se si vuole continuare a osservare una variabile, è possibile aggiungerla a una finestra **espressioni di controllo** da un DataTip. Fare clic con il pulsante destro del mouse sulla variabile in DataTip e selezionare Aggiungi espressione di **controllo**.

La variabile viene visualizzata nella finestra **espressioni di controllo** . Se l'edizione di Visual Studio supporta più di una finestra **espressioni di controllo** , la variabile viene visualizzata in espressione di **controllo 1**.

## <a name="import-and-export-datatips"></a>Importazione ed esportazione di suggerimenti dati

È possibile esportare i suggerimenti dati in un file XML, che è possibile condividere o modificare utilizzando un editor di testo. È anche possibile importare un file XML DataTip ricevuto o modificato.

**Per esportare i suggerimenti dati:**

1. Selezionare **debug**  >  **Esporta suggerimenti** dati.

1. Nella finestra di dialogo **Esporta suggerimenti** dati passare al percorso in cui salvare il file XML, digitare un nome per il file e quindi selezionare **Salva**.

**Per importare i suggerimenti dati:**

1. Selezionare **debug**  >  **Importa suggerimenti** dati.

1. Nella finestra di dialogo **Importa suggerimenti** dati selezionare il file XML dei suggerimenti dati che si desidera aprire e quindi selezionare **Apri**.

## <a name="see-also"></a>Vedi anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
