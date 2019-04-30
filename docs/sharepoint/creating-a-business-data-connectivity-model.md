---
title: Creazione di un Business Data Connectivity Model | Microsoft Docs
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
ms.openlocfilehash: 9f3da13858507a3ff176aaa0a44051674fd5285f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443553"
---
# <a name="create-a-business-data-connectivity-model"></a>Creare un modello di integrazione applicativa dei dati business
  È possibile creare un modello di integrazione applicativa dei dati (BDC) o personalizzare un modello di integrazione applicativa dei dati esistente con Visual Studio. Ogni progetto di SharePoint può contenere un solo modello. Per altre informazioni, vedere [integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Creare un nuovo modello
 Per creare un nuovo modello, creare un **Business Data Connectivity Model** del progetto oppure aggiungere un **Business Data Connectivity Model** voce a una **progetto SharePoint vuoto**.

> [!NOTE]
> È necessario disporre di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installato nel computer.

 Visual Studio aggiunge una cartella al progetto. Questa cartella contiene il nome specificato per il **Business Data Connectivity Model** degli elementi nella **Aggiungi nuovo elemento** nella finestra di dialogo. Se si crea una nuova **Business Data Connectivity Model** i nomi di progetto, Visual Studio nella cartella **BdcModel1**.

 Visual Studio aggiunge i seguenti file nella nuova cartella:

|File|Descrizione|
|----------|-----------------|
|File di definizione del modello|Contiene il codice XML che definisce le entità, metodi, oggetti di sistema Line-of-Business (LOB) e altri metadati che descrivono il modello.<br /><br /> Modificare i metadati in questo file usando la finestra di progettazione di integrazione applicativa dei dati, **Esplora integrazione Applicativa**, **Dettagli metodo BDC** finestra, e **proprietà** finestra.|
|File di codice di entità servizio|Contiene metodi che recuperano, aggiornano ed eliminano le istanze di entità predefinito.|

 Per definire le proprietà di un'entità, modificare il file di codice di entità. Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Per recuperare, aggiornare ed eliminare istanze di un'entità, aggiungere codice al file di codice servizio dell'entità. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quando si compila il progetto, Visual Studio crea un assembly. Assicurarsi di non aggiungere altri elementi al progetto con cui aggiungere codice per l'assembly del progetto (ad esempio: una **flusso di lavoro sequenziale** elemento o una **Web Part** elemento). Il codice per l'elemento non verrà eseguito quando si distribuisce la soluzione perché il pacchetto della soluzione non copiare l'assembly nella global assembly cache.  Il pacchetto della soluzione consente di distribuire l'assembly solo nel database di catalogo dati business in SharePoint.

> [!NOTE]
> Visual Studio consente di copiare l'assembly in entrambe le posizioni nel computer locale quando si esegue il debug del progetto.

## <a name="add-an-existing-model"></a>Aggiungere un modello esistente
 È possibile importare un modello che è stato creato usando altri strumenti, ad esempio SharePoint Designer. È possibile scegliere di importare un modello esistente al progetto nelle situazioni seguenti:

- Per personalizzare un modello che è già stato distribuito a una server farm di SharePoint.

- Per creare un pacchetto e distribuire un modello esistente in più server farm di SharePoint.

  In entrambi i casi, i sistemi LOB definiti nel modello importato non sono interessati e continueranno a funzionare come previsto. Per aggiungere un modello esistente a un progetto SharePoint, usare Visual Studio **Aggiungi elemento esistente** nella finestra di dialogo. Per altre informazioni, vedere [Procedura: Aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  È possibile aggiungere un sistema LOB di assembly del tipo di .NET Framework per il modello importato, selezionare un'opzione nel **LobSystem di assembly .NET aggiungere**. In questo modo sarà possibile scrivere codice personalizzato e usare una finestra di progettazione per definire i metadati per il modello importato.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)|Illustra come creare un nuovo modello di integrazione applicativa dei dati.|
|[Procedura: Aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Illustra come importare un modello esistente in un progetto SharePoint.|
|[Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Viene descritto come fornire stringhe da unire con i metadati del modello quando il modello viene utilizzato da una Web Part o una pagina Web.|
|[Procedura: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Illustra come includere un assembly personalizzato nella funzionalità.|
