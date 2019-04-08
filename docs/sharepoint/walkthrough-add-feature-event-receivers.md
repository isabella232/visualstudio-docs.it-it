---
title: 'Procedura dettagliata: Aggiungere ricevitori di eventi | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9701281ed6b6e84a3147d6fdeda9ce045fcb5305
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865294"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procedura dettagliata: Aggiungere ricevitori di eventi
  Ricevitori di eventi sono metodi che vengono eseguite quando si verifica uno degli eventi correlati alle funzionalità seguenti in SharePoint:

- Una funzionalità viene installata.

- Una funzionalità viene attivata.

- Una funzionalità viene disattivata.

- Una funzionalità è stata rimossa.

  Questa procedura dettagliata illustra come aggiungere un ricevitore di eventi a una funzionalità in un progetto SharePoint. Vengono illustrate le attività seguenti:

- Creazione di un progetto vuoto con un ricevitore di eventi.

- La gestione di **FeatureDeactivating** (metodo).

- Utilizzo del modello oggetto di progetto SharePoint per aggiungere un annuncio all'elenco degli annunci.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

-   Edizioni supportate di Microsoft Windows e SharePoint.

-   Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Creare un progetto di ricevitore di eventi di funzionalità
 In primo luogo, creare un progetto per contenere il ricevitore di eventi.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Per creare un progetto con un ricevitore di eventi

1.  Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.

2.  Espandere la **SharePoint** nodo sotto **Visual C#** o **Visual Basic**, quindi scegliere il **2010** nodo.

3.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.

     È consigliabile usare questo tipo di progetto per i ricevitori di eventi di funzionalità perché non presentano alcun modello di progetto.

4.  Nel **Name** immettere **FeatureEvtTest**e quindi scegliere il **OK** pulsante per visualizzare il **Personalizzazione guidata SharePoint**.

5.  Nel **specificare il livello di sito e la sicurezza per il debug** pagina, immettere l'URL per il sito di SharePoint server in cui si desidera aggiungere il nuovo elemento campo personalizzato o usare il percorso predefinito (http://\<*sistema nome*> /).

6.  Nel **qual è il livello di attendibilità per la soluzione SharePoint?** keychains le **Distribuisci come soluzione farm** pulsante di opzione.

     Per altre informazioni sulle soluzioni create mediante sandbox e soluzioni farm, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7.  Scegliere il **Finish** pulsante e quindi si noti che una funzionalità denominata Feature1 visualizzata sotto il **funzionalità** nodo.

## <a name="add-an-event-receiver-to-the-feature"></a>Aggiungere un ricevitore di eventi per la funzionalità
 Successivamente, aggiungere un ricevitore di eventi per la funzionalità e aggiungere il codice che viene eseguito quando questa caratteristica è disattivata.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Per aggiungere un ricevitore di eventi per la funzionalità

1.  Aprire il menu di scelta rapida per il nodo di funzionalità e quindi scegliere **aggiungere funzionalità** per creare una funzionalità.

2.  Sotto il **funzionalità** nodo, aprire il menu di scelta rapida **Feature1**e quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un ricevitore di eventi per la funzionalità.

     Verrà aggiunto un file di codice in Feature1. In questo caso, il file è denominato uno *Feature1.EventReceiver.cs* oppure *Feature1.EventReceiver.vb*, a seconda del linguaggio di sviluppo del progetto.

3.  Se il progetto è scritto in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], aggiungere il codice seguente nella parte superiore del ricevitore di eventi, se non è già presente:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  Classe del ricevitore di eventi contiene diversi metodi di commento che fungono da eventi. Sostituire il **FeatureDeactivating** metodo con il codice seguente:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Il ricevitore di eventi di funzionalità di test
 Successivamente, disattivare la funzionalità per testare se le **FeatureDeactivating** metodo restituisce un annuncio all'elenco di annunci di SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Per testare il ricevitore di eventi

1.  Impostare il valore del progetto **configurazione distribuzione attiva** proprietà **Nessuna attivazione**.

     Impostazione di questa proprietà impedisce la funzionalità di attivazione in SharePoint e consente di eseguire il debug di ricevitori di eventi. Per altre informazioni, vedere [soluzioni SharePoint Debug](../sharepoint/debugging-sharepoint-solutions.md).

2.  Scegliere il **F5** tasto per eseguire il progetto e distribuirlo in SharePoint.

3.  Nella parte superiore della pagina Web di SharePoint, aprire il **Azioni sito** menu, quindi scegliere **Impostazioni sito**.

4.  Sotto il **Azioni sito** sezione del **le impostazioni del sito** pagina, scegliere il **Gestisci caratteristiche sito** collegamento.

5.  Nel **funzionalità** pagina, scegliere il **Activate** accanto al **FeatureEvtTest Feature1** funzionalità.

6.  Nel **funzionalità** pagina, scegliere il **disattiva** accanto al **FeatureEvtTest Feature1** funzionalità e quindi scegliere il **disattivare questa funzionalità**  collegamento di conferma per disattivare la funzionalità.

7.  Scegliere il **Home** pulsante.

     Si noti che viene visualizzato un annuncio nel **annunci** Elenca dopo la disattivazione della funzionalità.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)