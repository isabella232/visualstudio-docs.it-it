---
title: Creazione di un modello di integrazione applicativa dei dati | Microsoft Docs
description: Creazione di un modello di integrazione applicativa dei dati o personalizzazione di un modello di integrazione applicativa dei dati esistente tramite Visual Studio. Ogni progetto SharePoint può contenere un solo modello.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0486ce6ac53850b1b607f9e7f859806cdc3ef8fe
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850468"
---
# <a name="create-a-business-data-connectivity-model"></a>Creare un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati o personalizzare un modello di integrazione applicativa dei dati esistente tramite Visual Studio. Ogni progetto SharePoint può contenere un solo modello. Per altre informazioni, vedere [integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Creare un nuovo modello
 Per creare un nuovo modello, creare un progetto di **modello di integrazione applicativa dei dati** o aggiungere un elemento del **modello di integrazione applicativa dei** dati a un **progetto SharePoint vuoto**.

> [!NOTE]
> È necessario aver [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installato nel computer.

 Visual Studio aggiunge una cartella al progetto. Questa cartella ha il nome specificato per l'elemento **modello di integrazione applicativa dei dati** nella finestra di dialogo **Aggiungi nuovo elemento** . Se si crea un nuovo progetto di **modello di integrazione applicativa dei dati** , Visual Studio denomina la cartella **BdcModel1**.

 Visual Studio aggiunge i file seguenti alla nuova cartella:

|File|Descrizione|
|----------|-----------------|
|File di definizione del modello|Contiene il codice XML che definisce le entità, i metodi, gli oggetti di sistema line-of-business (LOB) e altri metadati che descrivono il modello.<br /><br /> Modificare i metadati in questo file usando la finestra di progettazione dell'integrazione applicativa dei dati, l' **esplorazione di BDC**, **i dettagli del metodo BDC** e la finestra **proprietà** .|
|File di codice del servizio entità|Contiene metodi che recuperano, aggiornano ed eliminano istanze dell'entità predefinita.|

 Per definire le proprietà di un'entità, modificare il file di codice dell'entità. Per altre informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Per recuperare, aggiornare ed eliminare le istanze di un'entità, aggiungere il codice al file di codice del servizio Entity. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quando si compila il progetto, Visual Studio crea un assembly. Assicurarsi di non aggiungere altri elementi al progetto che aggiungono codice all'assembly del progetto (ad esempio, un elemento **del flusso di lavoro sequenziale** o un elemento **Web part** ). Il codice per l'elemento non viene eseguito quando si distribuisce la soluzione perché il pacchetto della soluzione non copia l'assembly nel Global Assembly Cache.  Il pacchetto della soluzione distribuisce l'assembly nel database BDC solo in SharePoint.

> [!NOTE]
> Quando si esegue il debug del progetto, Visual Studio copia l'assembly in entrambi i percorsi del computer locale.

## <a name="add-an-existing-model"></a>Aggiungere un modello esistente
 È possibile importare un modello creato utilizzando altri strumenti, ad esempio SharePoint Designer. È possibile scegliere di importare un modello esistente nel progetto nelle situazioni seguenti:

- Per personalizzare un modello già distribuito in un server farm di SharePoint.

- Per creare un pacchetto e distribuire un modello esistente in più server farm di SharePoint.

  In entrambi i casi, i sistemi LOB definiti nel modello importato non sono interessati e continueranno a funzionare come previsto. Per aggiungere un modello esistente a un progetto SharePoint, utilizzare la finestra di dialogo **Aggiungi elemento esistente** di Visual Studio. Per altre informazioni, vedere [procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  È possibile aggiungere un sistema LOB di tipo .NET Framework assembly al modello importato selezionando un'opzione nell' **aggiunta dell'assembly .NET LobSystem**. In questo modo è possibile scrivere codice personalizzato e utilizzare una finestra di progettazione per definire i metadati per il modello importato.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)|Viene illustrato come creare un nuovo modello di integrazione applicativa dei dati.|
|[Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Viene illustrato come importare un modello esistente in un progetto SharePoint.|
|[Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Viene descritto come fornire stringhe unite ai metadati del modello quando il modello viene utilizzato da una Web part o una pagina Web.|
|[Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Viene illustrato come includere un assembly personalizzato nella funzionalità.|
