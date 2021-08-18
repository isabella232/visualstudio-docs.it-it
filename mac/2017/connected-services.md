---
title: Servizi connessi
description: Aggiungere l'archiviazione dei dati di Azure, l'autenticazione e le notifiche push alle app per dispositivi mobili da Visual Studio per Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2018
ms.openlocfilehash: b33b6d3f0865ca338512f744f5b924ae2992179a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082543"
---
# <a name="connected-services-walkthrough"></a>Procedura dettagliata per Servizi connessi

Il flusso di lavoro Servizi connessi abilita il flusso di lavoro del portale di Azure in Visual Studio per Mac, in modo che non sia necessario lasciare il progetto per aggiungere servizi.

La procedura dettagliata illustra come aggiungere un servizio back-end di Azure che offre archiviazione dei dati cloud, autenticazione e notifiche push a un'applicazione di libreria di classi portabile Xamarin.Forms multipiattaforma.

1. Per prima cosa fare doppio clic sul nodo **Servizi connessi** della soluzione. Viene visualizzata la **raccolta servizi**.
  Si tratta di un elenco di servizi disponibili per il tipo di applicazione. Fare clic su un servizio, come ad esempio **Back-end dispositivi mobili con Servizio app di Azure**, per selezionarlo.

    [![Servizi connessi nodo in Visual Studio per Mac](media/connected-services-image001-sml.png "Servizi connessi nodo in Visual Studio per Mac")](media/connected-services-image001.png#lightbox)

2. La pagina Dettagli servizio contiene una descrizione del servizio e le dipendenze da installare.
  Fare clic sul pulsante **Aggiungi** per aggiungere le dipendenze per l'app:

    [![Back-end per dispositivi mobili con Azure](media/connected-services-image002-sml.png "Back-end per dispositivi mobili con Azure")](media/connected-services-image002.png#lightbox)

3. Perché funzionino, è necessario aggiungere le dipendenze sia alla libreria di classi portabile sia ai progetti specifici della piattaforma.
  Selezionare le caselle di controllo per aggiungere il servizio a ogni progetto che farà riferimento ad esso, direttamente o indirettamente:

    [![Controllare tutti i progetti che devono fare riferimento al servizio](media/connected-services-image003-sml.png "Controllare tutti i progetti che devono fare riferimento al servizio")](media/connected-services-image003.png#lightbox)

4. Scegliere **Accetta** nella finestra di dialogo **Accettazione della licenza** per i pacchetti NuGet.
  È possibile che vi siano due finestre di dialogo in cui selezionare l'accettazione, una per MobileClient e le dipendenze e l'altra per SQLiteStore, che è necessario per la sincronizzazione dei dati offline:

    [![Accettare contratti di licenza](media/connected-services-image004-sml.png "Accettare contratti di licenza")](media/connected-services-image004.png#lightbox)

    ![Finestra Accettazione della licenza](media/connected-services-image005.png "Finestra Accettazione della licenza")

5. Dopo aver aggiungono le dipendenze, verrà chiesto di accedere con l'account che si vuole usare per comunicare con Azure.
  Se si è già connessi con un ID Microsoft, Visual Studio per Mac tenta di recuperare le sottoscrizioni di Azure e tutti i servizi app ad esse associati. Se l'utente non ha sottoscrizioni, può aggiungerne registrandosi per una versione di prova gratuita o acquistando un piano di sottoscrizione nel portale di Azure.

6. Selezionare un servizio app dall'elenco. In questo modo il codice del modello per l'oggetto `MobileServiceClient` verrà compilato con l'URL corrispondente del servizio app in Azure:

    [![Selezionare il servizio app dall'elenco](media/connected-services-image006-sml.png "Selezionare il servizio app dall'elenco")](media/connected-services-image006.png#lightbox)

    Se non vi sono servizi elencati, fare clic sul pulsante **Nuovo** (vedere il passaggio 9).

7. Copiare il codice del modello per `MobileServiceClient` nella libreria di classi portabile. Il percorso del file non è importante, purché l'istanza sia una sola.
  L'approccio consigliato consiste nel creare una classe `AzureService` che gestisca tutte le interazioni di Azure e usi `MobileServiceClient`:

    ![Copiare il codice di configurazione nell'api](media/connected-services-image007.png "Copiare il codice di configurazione nell'app")

8. Seguire la documentazione in **Passaggi successivi** per aggiungere dati, la sincronizzazione offline, l'autenticazione e le notifiche push all'app:

    [![Esaminare le istruzioni dei passaggi successivi](media/connected-services-image008-sml.png "Esaminare le istruzioni dei passaggi successivi")](media/connected-services-image008.png#lightbox)

9. Se non si hanno servizi app esistenti, è possibile creare nuovi servizi in Visual Studio per Mac.
  Fare clic sul pulsante **Nuovo** nella parte inferiore sinistra dell'elenco di servizi per aprire la finestra di dialogo **Nuovo servizio app**:

    [![Creare un nuovo servizio app in Visual Studio per Mac](media/connected-services-image009-sml.png "Creare un nuovo servizio app in Visual Studio per Mac")](media/connected-services-image009.png#lightbox)

Il nuovo servizio richiede i parametri seguenti:

- **Nome del servizio app**: nome univoco/id del piano
- **Sottoscrizione**: la sottoscrizione che si vuole usare per pagare il servizio
- **Gruppo di risorse**: un modo per organizzare tutte le risorse di Azure per un progetto. È possibile usarne uno esistente o crearne uno nuovo. Se si tratta del primo servizio di Azure, crearne uno nuovo.
- **Piano di servizio**: determina la posizione e il costo delle risorse che lo usano. È possibile usarne uno esistente o crearne uno nuovo. Se si tratta del primo servizio di Azure, usare quello predefinito o crearne uno nuovo al livello gratuito (F1).

Per altre informazioni, vedere la [documentazione del servizio app di Azure](/azure/developer/mobile-apps/azure-mobile-apps/overview).

## <a name="see-also"></a>Vedi anche

- [Servizi connessi (Visual Studio in Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)
