---
title: Visualizzare i valori dei dati nei suggerimenti dati nell'editor del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 689d01c7e22cca430693a85e6dedcc7706fda41d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437696"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Visualizzare i valori di dati nei suggerimenti dati nell'editor del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente.  
  
 Nelle [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], i suggerimenti dati possono essere aggiunti a una posizione specifica in un file di origine, oppure possono scorrere nella parte superiore delle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Per visualizzare un suggerimento dati (solo in modalità di interruzione)  
  
1. In una finestra di origine, posizionare il puntatore del mouse su una qualsiasi variabile nell'ambito corrente.  
  
    Viene visualizzato un suggerimento dati.  
  
   > [!NOTE]
   > I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel punto in cui passa il cursore. Se si passa il puntatore su una variabile in un'altra funzione con lo stesso nome di una variabile presente nel contesto corrente, il valore della variabile nell'altra funzione viene visualizzato come valore della variabile nel contesto corrente.  
  
2. Il suggerimento dati scompare quando si rimuove il puntatore del mouse. Per bloccare il suggerimento dati, in modo che resti aperta, scegliere il **blocca a origine** icona, o  
  
   - Fare doppio clic su una variabile, quindi fare clic su **blocca a origine**.  
  
     Il suggerimento dati bloccato verrà chiuso al termine della sessione di debug.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Per sbloccare un suggerimento dati e far sì che scorra  
  
- In un suggerimento dati bloccato, scegliere il **Sblocca da origine** icona.  
  
     L'icona di blocco passa alla posizione sbloccata. Il suggerimento dati scorre ora nella parte superiore delle finestre aperte. Il suggerimento dati mobile verrà chiuso al termine della sessione di debug.  
  
### <a name="to-repin-a-floating-datatip"></a>Per ribloccare un suggerimento dati mobile  
  
- In un suggerimento dati fare clic sull'icona di blocco.  
  
     L'icona passa alla posizione bloccata. Se il suggerimento dati è al di fuori di una finestra di origine, l'icona di blocco è disabilitata e il suggerimento dati non può essere bloccato.  
  
### <a name="to-close-a-datatip"></a>Per chiudere un suggerimento dati  
  
- Posizionare il puntatore del mouse su un suggerimento dati e quindi scegliere il **Chiudi** icona.  
  
### <a name="to-close-all-datatips"></a>Per chiudere tutti i suggerimenti dati  
  
- Nel **Debug** menu, fare clic su **Cancella tutti i suggerimenti dati**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Per chiudere tutti i suggerimenti dati di un file specifico  
  
- Nel **Debug** menu, fare clic su **Cancella tutti i suggerimenti dati bloccati a** *File*.  
  
## <a name="expanding-and-editing-information"></a>Espansione e modifica delle informazioni  
 È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Per espandere una variabile per visualizzarne gli elementi  
  
- In un suggerimento dati posizionare il puntatore del mouse sul **+** sign che precede il nome della variabile.  
  
     La variabile si espande per visualizzare i relativi elementi in formato struttura ad albero.  
  
     Quando la variabile è espansa, è possibile utilizzare i tasti di direzione sulla tastiera per spostarsi verso l'alto e verso il basso. In alternativa, è possibile utilizzare il mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Per modificare il valore di una variabile utilizzando un suggerimento dati  
  
1. In un suggerimento dati, fare clic sul valore. Questa opzione non è disponibile per i valori di sola lettura.  
  
2. Digitare un nuovo valore e premere INVIO.  
  
## <a name="making-a-datatip-transparent"></a>Rendere trasparente un suggerimento dati  
 Per visualizzare il codice che sta dietro a un suggerimento dati, è possibile renderlo temporaneamente trasparente. Ciò non si applica a suggerimenti dati bloccati o mobili.  
  
#### <a name="to-make-a-datatip-transparent"></a>Per rendere trasparente un suggerimento dati  
  
- In un suggerimento dati, premere CTRL.  
  
     Il suggerimento dati resterà trasparente finché si terrà premuto il tasto CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Visualizzazione di tipi di dati complessi  
 Se viene visualizzata un'icona della lente di ingrandimento accanto al nome di una variabile in un suggerimento dati, uno o più [creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md) sono disponibili per le variabili di quel tipo di dati. È possibile utilizzare un visualizzatore per visualizzare le informazioni in un formato più significativo, generalmente grafico.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Per visualizzare il contenuto di una variabile utilizzando un visualizzatore  
  
- Fare clic sull'icona a forma di lente di ingrandimento per selezionare il visualizzatore predefinito per il tipo di dati.  
  
     -oppure-  
  
     Fare clic sulla freccia popup accanto al visualizzatore per selezionare da un elenco di visualizzatori appropriati per il tipo di dati.  
  
     Un visualizzatore visualizzerà le informazioni.  
  
## <a name="adding-information-to-a-watch-window"></a>Aggiunta di informazioni a una finestra Espressioni di controllo  
 Se si desidera continuare a guardare una variabile, è possibile aggiungere la variabile per il **Watch** finestra da un suggerimento dati.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Per aggiungere una variabile alla finestra Espressioni di controllo  
  
- Fare doppio clic su un suggerimento dati e quindi fare clic su **Aggiungi espressione di controllo**.  
  
     La variabile verrà aggiunta per il **Watch** finestra. Se si usa un'edizione che supporta più **Watch** windows, la variabile verrà aggiunta a **espressione di controllo 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importazione ed esportazione di suggerimenti dati  
 È possibile esportare suggerimenti dati in un file XML, per poi condividerlo con un collega o modificarlo mediante un editor di testo.  
  
#### <a name="to-export-datatips"></a>Per esportare suggerimenti dati  
  
1. Nel menu Debug, fare clic su **Esporta suggerimenti dati**.  
  
     Il **Esporta suggerimenti dati** verrà visualizzata la finestra di dialogo.  
  
2. Usare tecniche di file standard per passare al percorso in cui si desidera salvare il file XML, digitare un nome per il file nei **nomefile** casella e quindi fare clic su **OK**.  
  
#### <a name="to-import-datatips"></a>Per importare suggerimenti dati  
  
1. Nel menu Debug, fare clic su **Importa suggerimenti dati**.  
  
     Il **Importa suggerimenti dati** verrà visualizzata la finestra di dialogo.  
  
2. Utilizzare la finestra di dialogo per trovare il file XML che si desidera aprire e fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: Utilizzare la finestra di dialogo Controllo immediato](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: Modificare il formato numerico del Debugger Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
