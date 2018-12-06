---
title: Visualizzare i valori dei dati nei suggerimenti dati nell'editor del codice | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4156ff8f81e7a011aeff0cf753af60bb3d6cd924
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621539"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Visualizzare i valori dei dati nei suggerimenti dati nell'editor del codice

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [correggere i bug scrivendo meglio C# codice](../debugger/write-better-code-with-visual-studio.md) e [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

Se si tratta di debug per la prima volta, è possibile leggere [scrivere meglio C# di codice usando Visual Studio](../debugger/write-better-code-with-visual-studio.md) e [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di leggere questo articolo.
  
## <a name="work-with-datatips"></a>Lavorare con i suggerimenti dati

I suggerimenti dati vengono visualizzati solo in modalità di interruzione e solo in variabili che sono nell'ambito corrente di esecuzione.

### <a name="display-a-datatip"></a>Visualizzare un suggerimento dati  
  
1. Impostare un punto di interruzione nel codice e avviare il debug premendo **F5** o selezionando **Debug** > **Avvia debug**.
  
1. Quando sospesa in corrispondenza del punto di interruzione, passare il mouse su una qualsiasi variabile nell'ambito corrente. Viene visualizzato un suggerimento dati, che mostra il nome e il valore corrente della variabile.

### <a name="make-a-datatip-transparent"></a>Rendere trasparente un suggerimento dati  

Per rendere un suggerimento dati è trasparente per visualizzare il codice che è di sotto di esso, mentre nel suggerimento dati, premere **Ctrl**. Il suggerimento dati rimane trasparente, purché si tiene premuto il **Ctrl** chiave. Questo non funziona per i suggerimenti dati bloccati o mobili.  
### <a name="pin-a-datatip"></a>Aggiungi un suggerimento dati

Per aggiungere un suggerimento dati, in modo che rimanga aperta, selezionare la puntina da disegno **blocca a origine** icona. 

![Aggiungere un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "aggiungere un suggerimento dati")

È possibile spostare un suggerimento dati bloccato trascinandolo intorno alla finestra di codice. Viene visualizzata un'icona della puntina da disegno nella barra di navigazione accanto alla riga che viene aggiunto il suggerimento dati. 

>[!NOTE]
>I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non il cursore corrente o il percorso di suggerimento dati. Se passa il mouse su una variabile in un'altra funzione che ha lo stesso nome di una variabile nel contesto corrente, viene visualizzato il valore della variabile nel contesto corrente.
  
### <a name="unpin-a-datatip-from-source"></a>È possibile rimuovere un suggerimento dati dall'origine

Per float un suggerimento dati bloccato, il suggerimento dati del mouse e selezionare l'icona della puntina da disegno dal menu di scelta rapida. 

L'icona della puntina da disegno passa alla posizione sbloccata e il suggerimento dati ora viene spostata o possono essere trascinato sopra a tutte le finestre aperte. I suggerimenti dati a virgola mobile chiudono al termine della sessione di debug.  
  
### <a name="repin-a-datatip"></a>Ribloccare un suggerimento dati  
  
Per ribloccare un suggerimento dati mobile all'origine, passare il mouse su di esso nell'editor del codice e selezionare l'icona della puntina da disegno. L'icona della puntina da disegno passa alla posizione bloccata e il suggerimento dati anche in questo caso sia stato aggiunto solo alla finestra del codice. 

Se un suggerimento dati è mobile rispetto a una finestra del codice non di origine, non è disponibile l'icona della puntina da disegno, e non può essere riaggiunto il suggerimento dati. Per accedere a puntina da disegno, restituire il suggerimento dati alla finestra dell'editor di codice per trascinarlo, o che lo stato attivo la finestra di codice. 
  
### <a name="close-a-datatip"></a>Chiudere un suggerimento dati  
  
Per chiudere un suggerimento dati, il suggerimento dati del mouse e selezionare il tipo di chiusura (**x**) icona dal menu di scelta rapida.  
  
### <a name="close-all-datatips"></a>Chiudere tutti i suggerimenti dati  
  
Per chiudere tutti i suggerimenti dati, scegliere il **Debug** dal menu **Cancella tutti i suggerimenti dati**.  
  
### <a name="close-all-datatips-for-a-specific-file"></a>Chiudere tutti i suggerimenti dati per un file specifico  
  
Per chiudere tutti i suggerimenti dati per un file specifico, scegliere il **Debug** dal menu **Cancella tutti i suggerimenti dati bloccati a \<nomefile >**.  
  
## <a name="expand-and-edit-information"></a>Espandere e modificare le informazioni  
È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
### <a name="expand-a-variable"></a>Espandere una variabile

Per espandere un oggetto in un suggerimento dati per visualizzarne gli elementi, passare il mouse sulle frecce di espansione prima i nomi degli elementi da visualizzare gli elementi in formato ad albero. Per un suggerimento dati bloccato, selezionare la **+** prima che la variabile assegnare un nome e quindi espandere l'albero. 

![Espandere un suggerimento dati](../debugger/media/dbg-tour-data-tips.png "espandere un suggerimento dati")

È possibile utilizzare il mouse o i tasti di direzione sulla tastiera per spostarsi su e giù nella vista espansa. 

È anche possibile aggiungere elementi espansi per il suggerimento dati bloccato al passaggio del mouse su di essi e selezionando le relative icone puntina da disegno. Gli elementi visualizzati quindi il suggerimento dati bloccato dopo la compressione dell'albero. 

### <a name="edit-the-value-of-a-variable"></a>Modificare il valore di una variabile

Per modificare il valore di una variabile o un elemento in un suggerimento dati, selezionare il valore, digitare un nuovo valore e premere **invio**. Selezione è disabilitata per i valori di sola lettura.  

## <a name="visualize-complex-data-types"></a>Visualizzare i tipi di dati complessi  

Un'icona della lente di ingrandimento accanto a una variabile o un elemento in un suggerimento dati significa che uno o più [visualizzatori](../debugger/create-custom-visualizers-of-data.md), ad esempio le [Visualizzatore di testo](../debugger/string-visualizer-dialog-box.md), sono disponibili per la variabile. Visualizzatori di visualizzano le informazioni in modo più significativo, in alcuni casi con interfaccia grafico.
  
Per visualizzare l'elemento usando il visualizzatore predefinito per il tipo di dati, selezionare l'icona della lente di ingrandimento ![icona di Visualizzatore](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore"). Selezionare la freccia accanto all'icona della lente di ingrandimento per selezionare da un elenco di visualizzatori per il tipo di dati.  

## <a name="add-a-variable-to-a-watch-window"></a>Aggiungere una variabile a una finestra Espressioni di controllo  

Se si desidera continuare a guardare una variabile, è possibile aggiungerlo a un **Watch** finestra da un suggerimento dati. La variabile nel suggerimento dati e scegliere **Aggiungi espressione di controllo**. 

La variabile viene visualizzata nel **Watch** finestra. Se l'edizione di Visual Studio supporta più di uno **Watch** finestra, la variabile viene visualizzata nella **Watch1**. 
  
## <a name="import-and-export-datatips"></a>Importare ed esportare suggerimenti dati  

È possibile esportare suggerimenti dati in un file XML, che è possibile condividere o in un editor di testo di modifica. È anche possibile importare un file XML DataTip aver ricevuto o modificato. 
  
**Per esportare suggerimenti dati:** 
  
1. Selezionare **Debug** > **Esporta suggerimenti dati**.  
   
1. Nel **Esporta suggerimenti dati** della finestra di dialogo passare alla posizione in cui salvare il file XML, digitare un nome per il file e quindi selezionare **salvare**.  
  
**Per importare suggerimenti dati:** 
  
1. Selezionare **Debug** > **Importa suggerimenti dati**.  
   
1. Nel **Importa suggerimenti dati** finestra di dialogo, selezionare il file DataTips XML che si desidera aprire e quindi selezionare **aprire**.  

## <a name="see-also"></a>Vedere anche  
 [Che cos'è il debug?](../debugger/what-is-debugging.md)  
 [Correggere i bug scrivendo codice C# migliore](../debugger/write-better-code-with-visual-studio.md)  
 [Presentazione di debug](../debugger/debugger-feature-tour.md) [visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   

