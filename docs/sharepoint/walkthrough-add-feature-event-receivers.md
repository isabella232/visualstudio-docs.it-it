---
title: 'Procedura dettagliata: Aggiungere ricevitori di eventi | Microsoft Docs'
description: In questa procedura dettagliata aggiungere ricevitori di eventi di funzionalità, ovvero metodi che vengono eseguiti quando una funzionalità SharePoint viene installata, attivata, disattivata o rimossa.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 58e4210244c09271741a89e2343bfaf06a6d2c20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083999"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Procedura dettagliata: Aggiungere ricevitori di eventi di funzionalità
I ricevitori di eventi di funzionalità sono metodi che vengono eseguiti quando si verifica uno degli eventi correlati alle funzionalità seguenti SharePoint:

- È installata una funzionalità.

- Viene attivata una funzionalità.

- Una funzionalità viene disattivata.

- Una funzionalità viene rimossa.

Questa procedura dettagliata illustra come aggiungere un ricevitore di eventi a una funzionalità in un SharePoint progetto. Vengono illustrate le attività seguenti:

- Creazione di un progetto vuoto con un ricevitore di eventi di funzionalità.

- Gestione del **metodo FeatureDeactivating.**

- Uso del SharePoint a oggetti del progetto per aggiungere un annuncio all'elenco Annunci.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Creare un progetto ricevitore di eventi di funzionalità
 Creare prima di tutto un progetto per contenere il ricevitore di eventi della funzionalità.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Per creare un progetto con un ricevitore di eventi di funzionalità

1. Nella barra dei menu scegliere **File** nuovo Project  >    >   per visualizzare la **finestra di dialogo Project** nuovo file.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel riquadro **Modelli** scegliere il modello SharePoint **2010 Project** 2010.

     Questo tipo di progetto viene utilizzato per i ricevitori di eventi di funzionalità perché non hanno un modello di progetto.

4. Nella casella **Nome** immettere **FeatureEvtTest** e quindi scegliere **OK** per visualizzare la SharePoint **personalizzazione guidata**.

5. Nella pagina **Specificare** il sito e il livello di sicurezza per il debug immettere l'URL del sito del server SharePoint a cui si vuole aggiungere il nuovo elemento campo personalizzato o usare il percorso predefinito (http:// \<*system name*> /).

6. Nella sezione **Qual è il livello di attendibilità** SharePoint soluzione? scegliere il pulsante di opzione Distribuisci come **soluzione** farm.

     Per altre informazioni sulle soluzioni sandbox rispetto alle soluzioni farm, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. Scegliere il **pulsante** Fine e quindi osservare che nel nodo **Funzionalità** viene visualizzata una funzionalità denominata Feature1.

## <a name="add-an-event-receiver-to-the-feature"></a>Aggiungere un ricevitore di eventi alla funzionalità
 Aggiungere quindi un ricevitore di eventi alla funzionalità e aggiungere il codice che viene eseguito quando la funzionalità viene disattivata.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Per aggiungere un ricevitore di eventi alla funzionalità

1. Aprire il menu di scelta rapida per il nodo Funzionalità e quindi scegliere **Aggiungi funzionalità** per creare una funzionalità.

2. Nel nodo **Funzionalità** aprire il menu di scelta rapida per **Feature1** e quindi scegliere **Aggiungi** ricevitore di eventi per aggiungere un ricevitore di eventi alla funzionalità.

     Verrà aggiunto un file di codice in Feature1. In questo caso, è denominato *Feature1.EventReceiver.cs* o *Feature1.EventReceiver.vb,* a seconda del linguaggio di sviluppo del progetto.

3. Se il progetto è scritto in , aggiungere il codice seguente all'inizio del ricevitore di eventi, se non [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] è già presente:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs" id="Snippet1":::

4. La classe del ricevitore di eventi contiene diversi metodi commentati che fungono da eventi. Sostituire il **metodo FeatureDeactivating** con quanto segue:

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs" id="Snippet2":::

## <a name="test-the-feature-event-receiver"></a>Testare il ricevitore di eventi della funzionalità
 Disattivare quindi la funzionalità per verificare se il **metodo FeatureDeactivating** restituisce un annuncio SharePoint di annunci.

#### <a name="to-test-the-feature-event-receiver"></a>Per testare il ricevitore di eventi della funzionalità

1. Impostare il valore della proprietà Configurazione distribuzione attiva **del** progetto su **Nessuna attivazione**.

     L'impostazione di questa proprietà impedisce l'attivazione della funzionalità SharePoint e consente di eseguire il debug dei ricevitori di eventi di funzionalità. Per altre informazioni, vedere [Debug SharePoint soluzioni](../sharepoint/debugging-sharepoint-solutions.md).

2. Premere **F5 per** eseguire il progetto e distribuirlo SharePoint.

3. Nella parte superiore della pagina SharePoint Web aprire il menu **Azioni** sito e quindi scegliere **Impostazioni**.

4. Nella sezione **Azioni sito** della pagina **Impostazioni** sito scegliere il collegamento Gestisci **funzionalità sito.**

5. Nella pagina **Funzionalità** scegliere il pulsante **Attiva** accanto alla **funzionalità FeatureEvtTest Feature1.**

6. Nella pagina **Funzionalità** scegliere  il pulsante Disattiva accanto alla funzionalità **FeatureEvtTest Feature1** e quindi scegliere il collegamento **Disattiva** questa funzionalità per disattivare la funzionalità.

7. Scegliere il **pulsante Home.**

     Si noti che un annuncio viene visualizzato **nell'elenco Annunci** dopo la disattivazione della funzionalità.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)