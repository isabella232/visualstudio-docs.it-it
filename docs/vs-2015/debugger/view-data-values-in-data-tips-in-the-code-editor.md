---
title: Visualizzare i valori dei dati nei suggerimenti dati nell'editor di codice | Microsoft Docs
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
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700101"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Visualizzare i valori di dati nei suggerimenti dati nell'editor del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I suggerimenti dati sono un modo pratico per visualizzare le informazioni sulle variabili nel programma durante il debug. I suggerimenti dati funzionano solo in modalità di interruzione e solo con variabili che si trovano nell'ambito di esecuzione corrente.  
  
 In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] i suggerimenti dati possono essere aggiunti a una posizione specifica in un file di origine oppure possono essere mobili in tutte le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finestre.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Per visualizzare un suggerimento dati (solo in modalità di interruzione)  
  
1. In una finestra di origine, posizionare il puntatore del mouse su una qualsiasi variabile nell'ambito corrente.  
  
    Viene visualizzato un suggerimento dati.  
  
   > [!NOTE]
   > I suggerimenti dati vengono sempre valutati nel contesto in cui l'esecuzione viene sospesa, non nel punto in cui passa il cursore. Se si passa il puntatore su una variabile in un'altra funzione con lo stesso nome di una variabile presente nel contesto corrente, il valore della variabile nell'altra funzione viene visualizzato come valore della variabile nel contesto corrente.  
  
2. Il suggerimento dati scompare quando si rimuove il puntatore del mouse. Per aggiungere il DataTip in modo che rimanga aperto, fare clic sull'icona **Aggiungi a origine** o  
  
   - Fare clic con il pulsante destro del mouse su una variabile, quindi scegliere **Aggiungi a origine**.  
  
     Il suggerimento dati bloccato verrà chiuso al termine della sessione di debug.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Per sbloccare un suggerimento dati e far sì che scorra  
  
- In un DataTip aggiunto, fare clic sull'icona **Rimuovi dall'origine** .  
  
     L'icona di blocco passa alla posizione sbloccata. Il suggerimento dati scorre ora nella parte superiore delle finestre aperte. Il suggerimento dati mobile verrà chiuso al termine della sessione di debug.  
  
### <a name="to-repin-a-floating-datatip"></a>Per ribloccare un suggerimento dati mobile  
  
- In un suggerimento dati fare clic sull'icona di blocco.  
  
     L'icona passa alla posizione bloccata. Se il suggerimento dati è al di fuori di una finestra di origine, l'icona di blocco è disabilitata e il suggerimento dati non può essere bloccato.  
  
### <a name="to-close-a-datatip"></a>Per chiudere un suggerimento dati  
  
- Posizionare il puntatore del mouse su un DataTip, quindi fare clic sull'icona **Chiudi** .  
  
### <a name="to-close-all-datatips"></a>Per chiudere tutti i suggerimenti dati  
  
- Scegliere **Cancella tutti i suggerimenti**dati dal menu **debug** .  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Per chiudere tutti i suggerimenti dati di un file specifico  
  
- Scegliere **Cancella tutti i suggerimenti dati aggiunti al** *file*dal menu **debug** .  
  
## <a name="expanding-and-editing-information"></a>Espansione e modifica delle informazioni  
 È possibile utilizzare i suggerimenti dati per espandere una matrice, una struttura o un oggetto e visualizzarne i membri. È anche possibile modificare il valore di una variabile da un suggerimento dati.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Per espandere una variabile per visualizzarne gli elementi  
  
- In una DataTip, posizionare il puntatore del mouse sul **+** segno che precede il nome della variabile.  
  
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
 Se viene visualizzata un'icona a forma di lente di ingrandimento accanto al nome di una variabile in un DataTip, è possibile creare uno o più [visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md) per le variabili di tale tipo di dati. È possibile utilizzare un visualizzatore per visualizzare le informazioni in un formato più significativo, generalmente grafico.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Per visualizzare il contenuto di una variabile utilizzando un visualizzatore  
  
- Fare clic sull'icona a forma di lente di ingrandimento per selezionare il visualizzatore predefinito per il tipo di dati.  
  
     -oppure-  
  
     Fare clic sulla freccia popup accanto al visualizzatore per selezionare da un elenco di visualizzatori appropriati per il tipo di dati.  
  
     Un visualizzatore visualizzerà le informazioni.  
  
## <a name="adding-information-to-a-watch-window"></a>Aggiunta di informazioni a una finestra Espressioni di controllo  
 Se si vuole continuare a osservare una variabile, è possibile aggiungere la variabile alla finestra **espressioni di controllo** da un DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Per aggiungere una variabile alla finestra Espressioni di controllo  
  
- Fare clic con il pulsante destro del mouse su un DataTip, quindi scegliere Aggiungi espressione di **controllo**.  
  
     La variabile viene aggiunta alla finestra **espressioni di controllo** . Se si usa un'edizione che supporta più finestre **espressioni di controllo** , la variabile viene aggiunta a **espressioni di controllo 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importazione ed esportazione di suggerimenti dati  
 È possibile esportare suggerimenti dati in un file XML, per poi condividerlo con un collega o modificarlo mediante un editor di testo.  
  
#### <a name="to-export-datatips"></a>Per esportare suggerimenti dati  
  
1. Scegliere **Esporta suggerimenti**dati dal menu debug.  
  
     Verrà visualizzata la finestra di dialogo **Esporta suggerimenti** dati.  
  
2. Utilizzare le tecniche di file standard per passare al percorso in cui si desidera salvare il file XML, digitare un nome per il file nella casella **nome file** e quindi fare clic su **OK**.  
  
#### <a name="to-import-datatips"></a>Per importare suggerimenti dati  
  
1. Scegliere **Importa suggerimenti**dati dal menu debug.  
  
     Verrà visualizzata la finestra di dialogo **Importa suggerimenti** dati.  
  
2. Utilizzare la finestra di dialogo per trovare il file XML che si desidera aprire e fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: utilizzare la finestra di dialogo controllo immediato](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: modificare il formato numerico delle finestre del debugger](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
