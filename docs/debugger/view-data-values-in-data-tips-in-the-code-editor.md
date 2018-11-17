---
title: Visualizzare i valori dei dati nei suggerimenti dati nell'editor del codice | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
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
ms.openlocfilehash: afb318c8aa327345b3cd76ee16b718db1e0386aa
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826741"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Visualizzare i valori dei dati nei suggerimenti dati nell'editor del codice
I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [scrivere meglio C# di codice usando Visual Studio](../debugger/write-better-code-with-visual-studio.md) e [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.
  
### <a name="to-display-a-datatip"></a>Per visualizzare un suggerimento dati  
  
1. Impostare un punto di interruzione e avviare il debug (premere **F5**).

2. Dove la pausa nel debugger, posizionare il puntatore del mouse su una qualsiasi variabile nell'ambito corrente.
  
     Viene visualizzato un suggerimento dati.
  
3.  Il suggerimento dati scompare quando si rimuove il puntatore del mouse. Per bloccare il suggerimento dati, in modo che resti aperta, scegliere il **blocca a origine** icona o pulsante destro del mouse su una variabile, quindi fare clic su **blocca a origine**.

    ![L'aggiunta di un suggerimento dati](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel punto in cui passa il cursore. Se si passa il puntatore su una variabile in un'altra funzione con lo stesso nome di una variabile presente nel contesto corrente, il valore della variabile nell'altra funzione viene visualizzato come valore della variabile nel contesto corrente.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Per sbloccare un suggerimento dati e far sì che scorra  
  
-   In un suggerimento dati bloccato, scegliere il **Sblocca da origine** icona.  
  
     L'icona di blocco passa alla posizione sbloccata. Il suggerimento dati scorre ora nella parte superiore delle finestre aperte. Il suggerimento dati mobile verrà chiuso al termine della sessione di debug.  
  
### <a name="to-repin-a-floating-datatip"></a>Per ribloccare un suggerimento dati mobile  
  
-   In un suggerimento dati fare clic sull'icona di blocco.  
  
     L'icona passa alla posizione bloccata. Se il suggerimento dati è al di fuori di una finestra di origine, l'icona di blocco è disabilitata e il suggerimento dati non può essere bloccato.  
  
### <a name="to-close-a-datatip"></a>Per chiudere un suggerimento dati  
  
-   Posizionare il puntatore del mouse su un suggerimento dati e quindi scegliere il **Chiudi** icona.  
  
### <a name="to-close-all-datatips"></a>Per chiudere tutti i suggerimenti dati  
  
-   Nel **Debug** menu, fare clic su **Cancella tutti i suggerimenti dati**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Per chiudere tutti i suggerimenti dati di un file specifico  
  
-   Nel **Debug** menu, fare clic su **Cancella tutti i suggerimenti dati bloccati a** *File*.  
  
## <a name="expand-and-edit-information"></a>Espandere e modificare le informazioni  
 È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Per espandere una variabile per visualizzarne gli elementi  
  
-   In un suggerimento dati posizionare il puntatore del mouse sul **+** sign che precede il nome della variabile.  
  
    La variabile si espande per visualizzare i relativi elementi in formato ad albero.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "consente di visualizzare un suggerimento dati")
  
    Quando la variabile è espansa, è possibile utilizzare i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso. In alternativa, è possibile utilizzare il mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Per modificare il valore di una variabile utilizzando un suggerimento dati  
  
1.  In un suggerimento dati, fare clic sul valore. Questa opzione non è disponibile per i valori di sola lettura.  
  
2.  Digitare un nuovo valore e premere INVIO.  
  
## <a name="making-a-datatip-transparent"></a>Rendere trasparente un suggerimento dati  
 Per visualizzare il codice che sta dietro a un suggerimento dati, è possibile renderlo temporaneamente trasparente. Ciò non si applica a suggerimenti dati bloccati o mobili.  
  
#### <a name="to-make-a-datatip-transparent"></a>Per rendere trasparente un suggerimento dati  
  
-   In un suggerimento dati, premere CTRL.  
  
     Il suggerimento dati resterà trasparente finché si terrà premuto il tasto CTRL.  
  
## <a name="visualize-complex-data-types"></a>Visualizzare i tipi di dati complessi  
 Se viene visualizzata un'icona della lente di ingrandimento accanto al nome di una variabile in un suggerimento dati, uno o più [visualizzatori](../debugger/create-custom-visualizers-of-data.md), ad esempio le [i visualizzatori stringa](../debugger/string-visualizer-dialog-box.md), sono disponibili per le variabili di quel tipo di dati. È possibile utilizzare un visualizzatore per visualizzare le informazioni in un formato più significativo, generalmente grafico.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Per visualizzare il contenuto di una variabile utilizzando un visualizzatore  
  
-   Fare clic sull'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") per selezionare il visualizzatore predefinito per il tipo di dati.  
  
     oppure  
  
     Fare clic sulla freccia popup accanto al visualizzatore per selezionare da un elenco di visualizzatori appropriati per il tipo di dati.  
  
     Un visualizzatore visualizzerà le informazioni.  
  
## <a name="add-information-to-a-watch-window"></a>Aggiungere informazioni a una finestra Espressioni di controllo  
 Se si desidera continuare a guardare una variabile in una visualizzazione elenco, è possibile aggiungere la variabile per il **Watch** finestra da un suggerimento dati.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Per aggiungere una variabile alla finestra Espressioni di controllo  
  
-   Fare doppio clic su un suggerimento dati e quindi fare clic su **Aggiungi espressione di controllo**.  
  
     La variabile verrà aggiunta per il **Watch** finestra. Se si usa un'edizione che supporta più **Watch** windows, la variabile verrà aggiunta a **espressione di controllo 1.**  
  
## <a name="import-and-export-datatips"></a>Importare ed esportare suggerimenti dati  
 È possibile esportare suggerimenti dati in un file XML, per poi condividerlo con un collega o modificarlo mediante un editor di testo.  
  
#### <a name="to-export-datatips"></a>Per esportare suggerimenti dati  
  
1.  Nel menu Debug, fare clic su **Esporta suggerimenti dati**.  
  
     Il **Esporta suggerimenti dati** verrà visualizzata la finestra di dialogo.  
  
2.  Usare tecniche di file standard per passare al percorso in cui si desidera salvare il file XML, digitare un nome per il file nei **nomefile** casella e quindi fare clic su **OK**.  
  
#### <a name="to-import-datatips"></a>Per importare suggerimenti dati  
  
1.  Nel menu Debug, fare clic su **Importa suggerimenti dati**.  
  
     Il **Importa suggerimenti dati** verrà visualizzata la finestra di dialogo.  
  
2.  Utilizzare la finestra di dialogo per trovare il file XML che si desidera aprire e fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Ciò che sta eseguendo il debug?](../debugger/what-is-debugging.md)  
 [Scrivere meglio C# del codice con Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Presentazione di debug](../debugger/debugger-feature-tour.md) [visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Espressioni di controllo e controllo immediato Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   