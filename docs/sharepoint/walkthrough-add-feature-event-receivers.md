---
title: 'Procedura dettagliata: aggiungere ricevitori di eventi di funzionalità | Microsoft Docs'
description: In questa procedura dettagliata aggiungere ricevitori di eventi di funzionalità, ovvero metodi che vengono eseguiti quando una funzionalità di SharePoint viene installata, attivata, disattivata o rimossa.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c9d50de6630a813a9c8c7a075af6f921608fcd93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851530"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procedura dettagliata: aggiungere ricevitori di eventi di funzionalità
I ricevitori di eventi di funzionalità sono metodi che vengono eseguiti quando si verifica uno dei seguenti eventi correlati alle funzionalità in SharePoint:

- È installata una funzionalità di.

- Una funzionalità viene attivata.

- Una funzionalità è disattivata.

- Una funzionalità viene rimossa.

In questa procedura dettagliata viene illustrato come aggiungere un ricevitore di eventi a una funzionalità in un progetto SharePoint. Vengono illustrate le attività seguenti:

- Creazione di un progetto vuoto con un ricevitore di eventi di funzionalità.

- Gestione del metodo **FeatureDeactivating** .

- Utilizzo del modello a oggetti del progetto SharePoint per aggiungere un annuncio all'elenco degli annunci.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Creare un progetto di ricevitore di eventi di funzionalità
 Per prima cosa, creare un progetto che contenga il ricevitore di eventi di funzionalità.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Per creare un progetto con un ricevitore di eventi di funzionalità

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** .

2. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Nel riquadro **modelli** scegliere il modello di **progetto SharePoint 2010** .

     Questo tipo di progetto viene usato per i ricevitori di eventi di funzionalità perché non hanno un modello di progetto.

4. Nella casella **nome** immettere **FeatureEvtTest**, quindi scegliere il pulsante **OK** per visualizzare la **procedura guidata di personalizzazione di SharePoint**.

5. Nella pagina **specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito del server SharePoint a cui si desidera aggiungere il nuovo elemento campo personalizzato oppure utilizzare il percorso predefinito (http:// \<*system name*> /).

6. Nella sezione **Qual è il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm** .

     Per ulteriori informazioni sulle soluzioni create mediante sandbox e sulle soluzioni farm, vedere Considerazioni sulle soluzioni [create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7. Scegliere il pulsante **fine** , quindi osservare che una funzionalità denominata Feature1 viene visualizzata nel nodo **funzionalità** .

## <a name="add-an-event-receiver-to-the-feature"></a>Aggiungere un ricevitore di eventi alla funzionalità
 Successivamente, aggiungere un ricevitore di eventi alla funzionalità e aggiungere il codice che viene eseguito quando la funzionalità è disattivata.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Per aggiungere un ricevitore di eventi alla funzionalità

1. Aprire il menu di scelta rapida per il nodo funzionalità, quindi scegliere **Aggiungi funzionalità** per creare una funzionalità.

2. Nel nodo **funzionalità** aprire il menu di scelta rapida per **Feature1**, quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un ricevitore di eventi alla funzionalità.

     Viene aggiunto un file di codice in Feature1. In questo caso, il nome è *Feature1.EventReceiver.cs* o *Feature1. EventReceiver. vb*, a seconda del linguaggio di sviluppo del progetto.

3. Se il progetto è scritto in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , aggiungere il codice seguente all'inizio del ricevitore di eventi, se non è già presente:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. La classe Receiver dell'evento contiene diversi metodi impostati come commento che fungono da eventi. Sostituire il metodo **FeatureDeactivating** con il codice seguente:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Testare il ricevitore di eventi di funzionalità
 Disattivare quindi la funzionalità per verificare se il metodo **FeatureDeactivating** restituisce un annuncio all'elenco degli annunci di SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Per testare il ricevitore di eventi di funzionalità

1. Impostare il valore della proprietà di **configurazione della distribuzione attiva** del progetto su **No Activation**.

     L'impostazione di questa proprietà impedisce l'attivazione della funzionalità in SharePoint e consente di eseguire il debug dei ricevitori di eventi di funzionalità. Per ulteriori informazioni, vedere [debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2. Premere il tasto **F5** per eseguire il progetto e distribuirlo in SharePoint.

3. Nella parte superiore della pagina Web di SharePoint aprire il menu **Azioni sito** , quindi scegliere **Impostazioni sito**.

4. Nella sezione **Azioni sito** della pagina **Impostazioni sito** scegliere il collegamento **Gestisci caratteristiche sito** .

5. Nella pagina **funzionalità** fare clic sul pulsante **attiva** accanto alla funzionalità **FeatureEvtTest Feature1** .

6. Nella pagina **funzionalità** , scegliere il pulsante **Disattiva** accanto alla funzionalità **FeatureEvtTest Feature1** , quindi scegliere il collegamento Disattiva la conferma della **funzionalità** per disattivare la funzionalità.

7. Scegliere il pulsante **Home** .

     Si noti che un annuncio viene visualizzato nell'elenco **annunci** dopo che la funzionalità è stata disattivata.

## <a name="see-also"></a>Vedi anche

- [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)