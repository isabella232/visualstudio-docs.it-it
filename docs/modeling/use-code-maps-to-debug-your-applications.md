---
title: Usare le mappe codice per eseguire il debug delle applicazioni
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e01857878f927c619529d3bbfc63728f84f0b81d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594110"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Usare le mappe codice per eseguire il debug delle applicazioni

Le mappe codice consentono di evitare di perdersi nelle codebase di grandi dimensioni, nel codice con cui si ha poca familiarità o nel codice legacy. Ad esempio, quando si esegue il debug, potrebbe essere necessario esaminare il codice in molti file e progetti. Usare le mappe codice per esplorare queste parti di codice e comprendere le relazioni tra loro. In questo modo, non è necessario tenere traccia di questo codice a mente o creare un diagramma separato. Se il lavoro viene interrotto, le mappe codice consentono di aggiornare la memoria relativa al codice usato.

![&#45; Mapping della mappa del codice relazioni nel codice](../modeling/media/codemapstoryboardpaint.png)

**Una freccia verde indica il punto in cui viene visualizzato il cursore nell'editor**

Per informazioni dettagliate dei comandi e le azioni è possibile usare quando si lavora con le mappe codici, vedere [cercare e ridisporre le mappe codice](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Per creare e modificare le mappe del codice, è necessario Visual Studio Enterprise Edition. Nelle edizioni community e Professional di Visual Studio è possibile aprire i diagrammi generati in Enterprise Edition, ma non modificarli.

## <a name="understand-the-problem"></a>Informazioni sul problema
 Si supponga che sia presente un bug in un programma di disegno su cui si sta lavorando. Per riprodurre il bug, aprire la soluzione in Visual Studio e premere **F5** per avviare il debug.

 Quando si traccia una linea e si sceglie **Annulla l'ultimo tratto**, non viene eseguita alcuna operazione fino a quando non si traccia la riga successiva.

 ![Bug ripetizione &#45; mappa codice](../modeling/media/codemapstoryboardpaint0.png)

 Di conseguenza, iniziare l'analisi cercando il metodo `Undo`. Il metodo si trova nella classe `PaintCanvas`.

 ![Mappa &#45; del codice trovare il codice](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Avviare il mapping del codice
 A questo punto è possibile avviare il mapping del metodo `undo` e le relative relazioni. Nell'editor di codice aggiungere il metodo `undo` e i campi a cui viene fatto riferimento a una nuova mappa codici. Quando si crea una nuova mappa, l'indicizzazione del codice potrebbe richiedere del tempo. Ciò consente alle operazioni successive di essere eseguite più velocemente.

 ![Mappa &#45; del codice visualizzare il metodo e i campi correlati](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> L'evidenziazione verde indica gli ultimi elementi aggiunti alla mappa. La freccia verde indica la posizione del cursore nel codice. Le frecce tra gli elementi rappresentano relazioni diverse. È possibile ottenere altre informazioni sugli elementi nella mappa spostandovi sopra il mouse ed esaminando le relative descrizioni comandi.

 ![Mappa &#45; del codice Mostra descrizioni comandi](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Passare al codice ed esaminarlo dal mapping
 Per visualizzare la definizione di codice per ogni campo, fare doppio clic sul campo nella mappa o selezionare il campo e premere **F12**. La freccia verde si sposta tra gli elementi nella mappa. Il cursore nell'editor di codice viene spostato automaticamente.

 ![Mappa &#45; del codice esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5.png)

 ![Mappa &#45; del codice esaminare la definizione di campo](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> È inoltre possibile spostare la freccia verde sulla mappa spostando il cursore nell'editor di codice.

## <a name="understand-relationships-between-pieces-of-code"></a>Informazioni sulle relazioni tra parti di codice
 A questo punto si desidera sapere quale altro codice interagisce con i campi `history` e `paintObjects`. È possibile aggiungere tutti i metodi che fanno riferimento a questi campi alla mappa. Questa operazione può essere eseguita dalla mappa o dall'editor di codice.

 ![Mappa &#45; del codice trovare tutti i riferimenti](../modeling/media/codemapstoryboardpaint6.png)

 ![Aprire una mappa del codice nell'editor del codice](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Se si aggiungono elementi da un progetto condiviso in più applicazioni, ad esempio Windows Phone o Windows Store, tali elementi vengono sempre visualizzati nella mappa insieme al progetto di app attualmente attivo. Se pertanto si modifica il contesto in un altro progetto di app, il contesto nella mappa viene modificato anche per tutti gli elementi appena aggiunti dal progetto condiviso. Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.

 Modificare il layout per ridisporre il flusso di relazioni e rendere la mappa più facile da leggere. È inoltre possibile spostare elementi nella mappa trascinandoli.

 ![Layout delle &#45; modifiche della mappa codice](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Per impostazione predefinita, il **Layout incrementale** è attivato. Ciò consente di ridisporre la mappa il meno possibile quando vengono aggiunti nuovi elementi. Per ridisporre l'intera mappa ogni volta che si aggiungono nuovi elementi, disabilitare **Layout incrementale**.

 ![Layout delle &#45; modifiche della mappa codice](../modeling/media/codemapstoryboardpaint7.png)

 Esaminiamo questi metodi. Nella mappa fare doppio clic sul metodo **sul PaintCanvas** oppure selezionare questo metodo e premere **F12**. Questo metodo crea `history` e `paintObjects` come elenchi vuoti.

 ![Mappa &#45; del codice esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint8.png)

 A questo punto, ripetere gli stessi passaggi per esaminare la definizione del metodo `clear`. Il metodo `clear` esegue alcune attività con `paintObjects` e `history` e quindi chiama il metodo `Repaint`.

 ![Mappa &#45; del codice esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint9.png)

 A questo punto, esaminare la definizione del metodo `addPaintObject`. Tale metodo esegue alcune attività con `history` e `paintObjects`. e chiama inoltre `Repaint`.

 ![Mappa &#45; del codice esaminare la definizione del metodo](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Individuare il problema esaminando il mapping
 Sembra che tutti i metodi che modificano `history` e `paintObjects` chiamino `Repaint`. Tuttavia il metodo `undo` non chiama `Repaint`, anche se `undo` modifica gli stessi campi. Pertanto, è possibile risolvere il problema chiamando `Repaint` da `undo`.

 ![Mappa &#45; del codice trovare la chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint11.png)

 Se non fosse stata disponibile una mappa che mostrava questa chiamata mancante, sarebbe stato più difficile individuare il problema, specialmente in caso di codice più complesso.

## <a name="share-your-discovery-and-next-steps"></a>Condividere l'individuazione e passaggi successivi
 Prima che l'utente o un altro sviluppatore corregga il bug, è possibile inserire note nella mappa sul problema e su come correggerlo.

 ![Commento della &#45; Mappa del codice ed elementi del flag per il completamento](../modeling/media/codemapstoryboardpaint12.png)

 Ad esempio, è possibile aggiungere commenti alla mappa e contrassegnare gli elementi usando i colori.

 ![Mappa &#45; codice-elementi commentati e contrassegnati](../modeling/media/codemapstoryboardpaint12a.png)

 Se Microsoft Outlook è installato, è possibile inviare la mappa ad altre persone tramite posta elettronica. È inoltre possibile esportare la mappa come un'immagine o in un altro formato.

 ![Condivisione mappa &#45; codice, esportazione, posta elettronica](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Correggere il problema e visualizzare le operazioni effettuate
 Per correggere il bug, aggiungere la chiamata per `Repaint` a `undo`.

 ![Mappa &#45; del codice aggiunta della chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint14.png)

 Per confermare la correzione, riavviare la sessione di debug e tentare di riprodurre il bug. Ora scegliere **Annulla l'ultimo tratto** funziona come previsto e conferma che è stata apportata la correzione corretta.

 ![Mappa &#45; del codice confermare la correzione del codice](../modeling/media/codemapstoryboardpaint15.png)

 È possibile aggiornare la mappa per mostrare la correzione apportata.

 ![Mappa di &#45; aggiornamento della mappa codici con chiamata al metodo mancante](../modeling/media/codemapstoryboardpaint16.png)

 La mappa mostra ora un collegamento tra **Annulla** e **ridisegna**.

 ![Mappa codice &#45; aggiornata mappa con chiamata al metodo](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Quando si aggiorna la mappa, è possibile che venga visualizzato un messaggio che indica che l'indice di codice usato per creare la mappa è stato aggiornato. Ciò significa che un utente ha modificato il codice e di conseguenza la mappa non corrisponde al codice corrente. L'aggiornamento della mappa non verrà arrestato, ma potrebbe essere necessario ricreare la mappa per confermare che corrisponde al codice.

 A questo punto è stata eseguita l'analisi. Il problema è stato individuato e corretto eseguendo il mapping del codice. Si dispone inoltre di una mappa che consente di spostarsi nel codice e di ricordare quanto indicato e che mostra i passaggi eseguiti per correggere il problema.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping dei metodi nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Visualizzare il codice](../modeling/visualize-code.md)
