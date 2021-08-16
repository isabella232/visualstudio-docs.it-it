---
title: Visualizzare i valori delle variabili nei suggerimenti dati | Microsoft Docs
description: Usare i suggerimenti dati per visualizzare facilmente le informazioni sulle variabili, incluse le matrici e le strutture, durante il debug. È anche possibile modificare i valori.
ms.custom: SEO-VS-2020
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3ca70d8b77ff0ff0cb229207b433d402c96985c4dd0931268007930474ae26b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418863"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Visualizzare i valori dei dati nei suggerimenti dati nell'editor di codice

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente. Se è la prima volta che si prova a eseguire [](../debugger/debugging-absolute-beginners.md) il debug del codice, è possibile leggere Debug per principianti assoluti e Tecniche e strumenti di debug prima di procedere con questo articolo. [](../debugger/write-better-code-with-visual-studio.md)

## <a name="work-with-datatips"></a>Usare i suggerimenti dati

I suggerimenti dati vengono visualizzati solo in modalità di interruzione e solo nelle variabili nell'ambito di esecuzione corrente.

### <a name="display-a-datatip"></a>Visualizzare un suggerimento dati

1. Impostare un punto di interruzione nel codice e avviare il debug premendo **F5** o selezionando **Debug**  >  **Avvia debug.**

1. Quando viene sospeso in corrispondenza del punto di interruzione, passare il mouse su qualsiasi variabile nell'ambito corrente. Viene visualizzato un suggerimento dati che mostra il nome e il valore corrente della variabile.

### <a name="make-a-datatip-transparent"></a>Rendere trasparente un suggerimento dati

Per rendere trasparente un suggerimento dati per visualizzare il codice sottostante, mentre nel suggerimento dati premere **CTRL**. Il suggerimento dati rimane trasparente finché si tiene premuto **CTRL.** Questa operazione non funziona per i suggerimenti dati bloccati o mobili.
### <a name="pin-a-datatip"></a>Aggiungere un suggerimento dati

Per aggiungere un suggerimento dati in modo che rimanga aperto, selezionare l'icona a forma di puntina da disegno **Aggiungi all'origine.**

![Aggiungere un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "Aggiungere un suggerimento dati")

È possibile spostare un suggerimento dati bloccato trascinandolo nella finestra del codice. Nella barra accanto alla riga a cui è aggiunto il suggerimento dati viene visualizzata un'icona a forma di puntina da disegno.

>[!NOTE]
>I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel cursore corrente o nella posizione del suggerimento dati. Se si passa il mouse su una variabile in un'altra funzione con lo stesso nome di una variabile nel contesto corrente, viene visualizzato il valore della variabile nel contesto corrente.

### <a name="unpin-a-datatip-from-source"></a>Rimuovere un suggerimento dati dall'origine

Per rendere mobile un suggerimento dati aggiunto, passare il puntatore del mouse sul suggerimento dati e selezionare l'icona della puntina da disegno dal menu di scelta rapida.

L'icona a forma di puntina da disegno cambia in posizione bloccata e il suggerimento dati ora mobile o trascinato sopra tutte le finestre aperte. I suggerimenti dati mobili si chiudono al termine della sessione di debug.

### <a name="repin-a-datatip"></a>Rietichette un suggerimento dati

Per aggiungere nuovamente un suggerimento dati mobile all'origine, passare il puntatore del mouse su di esso nell'editor di codice e selezionare l'icona della puntina da disegno. L'icona della puntina da disegno cambia in posizione bloccata e il suggerimento dati viene nuovamente aggiunto solo alla finestra del codice.

Se un suggerimento dati è mobile su una finestra del codice non sorgente, l'icona a forma di puntina da disegno non è disponibile e il suggerimento dati non può essere aggiunto nuovamente. Per accedere all'icona della puntina da disegno, restituire il suggerimento dati alla finestra dell'editor del codice trascinandolo o attivando la finestra del codice.

### <a name="close-a-datatip"></a>Chiudere un suggerimento dati

Per chiudere un suggerimento dati, passare il puntatore del mouse sul suggerimento dati e selezionare l'icona di chiusura (**x**) dal menu di scelta rapida.

### <a name="close-all-datatips"></a>Chiudere tutti i suggerimenti dati

Per chiudere tutti i suggerimenti dati, **scegliere** Cancella tutti i suggerimenti dati dal menu **Debug.**

### <a name="close-all-datatips-for-a-specific-file"></a>Chiudere tutti i suggerimenti dati per un file specifico

Per chiudere tutti i suggerimenti dati per un file specifico, scegliere Cancella tutti i suggerimenti dati aggiunti a dal **menu** **Debug. \<Filename>**

## <a name="expand-and-edit-information"></a>Espandere e modificare le informazioni
È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.

### <a name="expand-a-variable"></a>Espandere una variabile

Per espandere un oggetto in un suggerimento dati per visualizzarne gli elementi, passare il mouse sulle frecce di espansione prima dei nomi degli elementi per visualizzare gli elementi in formato albero. Per un suggerimento dati bloccato, selezionare prima **+** del nome della variabile e quindi espandere l'albero.

![Espandere un suggerimento dati](../debugger/media/dbg-tour-data-tips.png "Espandere un suggerimento dati")

È possibile usare il mouse o i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso nella visualizzazione espansa.

È anche possibile aggiungere elementi espansi al suggerimento dati aggiunto passando il puntatore su di essi e selezionando le icone della puntina da disegno. Gli elementi vengono quindi visualizzati nel suggerimento dati bloccato dopo la compressione dell'albero.

### <a name="edit-the-value-of-a-variable"></a>Modificare il valore di una variabile

Per modificare il valore di una variabile o di un elemento in un suggerimento dati, selezionare il valore, digitare un nuovo valore e premere **INVIO.** La selezione è disabilitata per i valori di sola lettura.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Aggiungere proprietà nei suggerimenti dati

> [!NOTE]
> Questa funzionalità è supportata per .NET Core 3.0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nei suggerimenti dati con lo **strumento Aggiungi proprietà.**  Per usare questo strumento, passare il puntatore del mouse su una  proprietà e selezionare l'icona a forma di puntina visualizzata o fare clic con il pulsante destro del mouse e scegliere l'opzione Aggiungi membro come preferito nel menu di scelta rapida risultante.  Questa proprietà viene visualizzata nella parte superiore dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella colonna destra del suggerimento dati.  Per rimuovere una proprietà, selezionare di nuovo l'icona aggiungi o selezionare l'opzione Rimuovi membro **come** preferito nel menu di scelta rapida.

![Aggiunta di una proprietà in un suggerimento dati](../debugger/media/basic-pin-datatip.gif "Aggiunta di una proprietà in un suggerimento dati")

È anche possibile attivare o disattivare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto in un suggerimento dati.  È possibile accedere a entrambe le opzioni facendo  clic con il  pulsante destro del mouse su una riga contenente una proprietà e selezionando le opzioni Mostra solo membri aggiunti o Nascondi nomi di membri bloccati nei valori nel menu di scelta rapida.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualizzare tipi di dati complessi

Un'icona a forma di lente di ingrandimento accanto a [](../debugger/create-custom-visualizers-of-data.md)una variabile o a un elemento in un suggerimento dati significa che uno o più visualizzatori, ad esempio visualizzatore di [testo,](../debugger/string-visualizer-dialog-box.md)sono disponibili per la variabile. I visualizzatori visualizzano le informazioni in modo più significativo, a volte grafico.

Per visualizzare l'elemento usando il visualizzatore predefinito per il tipo di dati, selezionare l'icona della lente di ingrandimento ![Icona visualizzatore](../debugger/media/dbg-tips-visualizer-icon.png "Icona visualizzatore"). Selezionare la freccia accanto all'icona della lente di ingrandimento per selezionare il tipo di dati da un elenco di visualizzatori.

## <a name="add-a-variable-to-a-watch-window"></a>Aggiungere una variabile a un finestra Espressioni di controllo

Se si vuole continuare a controllare una variabile, è possibile aggiungerla a una finestra **Espressioni** di controllo da un suggerimento dati. Fare clic con il pulsante destro del mouse sulla variabile nel suggerimento dati e **scegliere Aggiungi espressioni di controllo.**

La variabile viene visualizzata nella **finestra Espressioni di** controllo. Se l Visual Studio edition supporta più di una finestra **Espressioni di** controllo, la variabile viene visualizzata in Espressioni di **controllo 1.**

## <a name="import-and-export-datatips"></a>Importare ed esportare suggerimenti dati

È possibile esportare i suggerimenti dati in un file XML, che è possibile condividere o modificare usando un editor di testo. È anche possibile importare un file XML del suggerimento dati ricevuto o modificato.

**Per esportare i suggerimenti dati:**

1. Selezionare **Debug**  >  **Esporta suggerimenti dati**.

1. Nella finestra **di dialogo Esporta** suggerimenti dati passare al percorso in cui salvare il file XML, digitare un nome per il file e quindi selezionare **Salva**.

**Per importare suggerimenti dati:**

1. Selezionare **Debug**  >  **Importa suggerimenti dati**.

1. Nella finestra **di dialogo Importa suggerimenti** dati selezionare il file XML dei suggerimenti dati che si vuole aprire e quindi selezionare **Apri.**

## <a name="see-also"></a>Vedi anche
- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Prima analisi del debug](../debugger/debugger-feature-tour.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
