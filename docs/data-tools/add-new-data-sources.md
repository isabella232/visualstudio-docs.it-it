---
title: Aggiungere nuove origini dati
description: Aggiungere nuove origini dati in Visual Studio. Un'origine dati è un oggetto .NET che si connette a un archivio dati e rende i dati disponibili per un'applicazione .NET.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a377acba7b8c64503e5e5f821b5f3f833a8d73b2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308051"
---
# <a name="add-new-data-sources"></a>Aggiungere nuove origini dati

:::moniker range=">=vs-2019"
> [!NOTE]
> Le funzionalità descritte in questo articolo si applicano .NET Framework Windows Forms e allo sviluppo WPF. Le funzionalità non sono supportate per lo sviluppo .NET Core, sia per WPF che per Windows Forms.
:::moniker-end

Nel contesto di strumenti di dati .NET in Visual Studio, il termine *data source* fa riferimento a oggetti .NET che si connettono a un archivio dati e rendere i dati disponibili a un'applicazione .NET. Le finestre di progettazione di Visual Studio possono usare l'output dell'origine dati per generare il codice boilerplate che associa i dati a un form quando si trascinano gli oggetti di database dalla finestra **Data Source**. Questo tipo di origine dati può essere:

- Classe in un Entity Framework modello associato a un tipo di database.

- Set di dati associato a un tipo di database.

- Classe che rappresenta un servizio di rete, ad esempio un servizio Windows Communication Foundation (WCF) o un servizio REST.

- Classe che rappresenta un servizio SharePoint.

- Classe o raccolta nella soluzione.

> [!NOTE]
> Se non si usano funzionalità di data binding, set di dati, Entity Framework, LINQ to SQL, WCF o SharePoint, il concetto di "origine dati" non è applicabile. È sufficiente connettersi direttamente al database usando gli oggetti SQLCommand e comunicare direttamente con il database.

È possibile creare e modificare le origini dati usando la **Configurazione guidata** origine dati in un'applicazione Windows Forms o Windows Presentation Foundation dati. Per Entity Framework, creare prima di tutto le classi di entità e quindi avviare la procedura guidata selezionando Project Add New Data Source (Aggiungi nuova origine dati) più avanti  >   in questo articolo.

![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Finestra Origini dati

Dopo aver creato un'origine dati, viene visualizzato nei **Data source** finestra degli strumenti.

> [!TIP]
> Per aprire la finestra **Data source**, assicurarsi che il progetto sia aperto e quindi premere **MAIUSC**+**Alt**+**1!d** oppure scegliere **View** > **Other Windows** > **Data source**.

È possibile trascinare un'origine dati dal **Data source** finestra in un'area di progettazione form o controllo. In questo modo viene generato codice boilerplate che visualizza i dati dall'archivio dati.

La figura seguente mostra un set di dati rilasciato in un Windows Form. Se si seleziona **F5** nell'applicazione, i dati del database sottostante vengono visualizzati nei controlli del modulo.

![Operazione di trascinamento dell'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origine dati per un database o un file di database

È possibile creare un set di dati o un modello Entity Framework da usare come origine dati per un database o un file di database.

### <a name="dataset"></a>Set di dati

Per creare un set di dati come origine dati, eseguire la Configurazione guidata origine **dati** selezionando **Progetto** Aggiungi nuova  >  **origine dati**. Scegliere il **tipo** di origine dati Database e seguire le istruzioni per specificare una connessione di database nuova o esistente o un file di database.

### <a name="entity-classes"></a>Classi di entità

Per creare un Entity Framework modello come origine dati:

1. Eseguire la **Entity Data Model guidata per** creare le classi di entità. Selezionare **Progetto**  >  **Aggiungi nuovo elemento**  >  **ADO.NET Entity Data Model**.

   ![Nuovo Entity Framework progetto di modello](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Scegliere il metodo in base al quale si vuole generare il modello.

   ![Entity Data Model (procedura guidata)](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Aggiungere il modello come origine dati. Le classi generate vengono visualizzate nella **Configurazione guidata origine dati** quando si sceglie la **categoria** Oggetti .

   ![Configurazione guidata origine dati con classi di entità](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origine dati per un servizio

Per creare un'origine dati da un servizio, eseguire la Configurazione guidata origine **dati** e scegliere il **tipo di** origine dati Servizio. Si tratta semplicemente di un collegamento alla **finestra di dialogo Aggiungi riferimento al servizio,** a cui è possibile accedere anche facendo clic con il pulsante destro del mouse sul progetto **in** Esplora soluzioni e selezionando Aggiungi **riferimento al servizio**.

Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto. Visual Studio crea anche oggetti proxy che corrispondono agli oggetti restituiti dal servizio. Ad esempio, un servizio che restituisce un set di dati viene rappresentato nel progetto come set di dati. Un servizio che restituisce un tipo specifico è rappresentato nel progetto come tipo restituito.

È possibile creare un'origine dati dai tipi di servizi seguenti:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servizi WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Servizi Web

    > [!NOTE]
    > Gli elementi visualizzati nei **Data source** finestra dipendono i dati restituiti al servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, viene visualizzato alcun elemento nel **Data source** finestra una volta completata la procedura guidata. Ciò è dovuto al fatto che i set di dati non tipizzati non forniscono uno schema e pertanto la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

## <a name="data-source-for-an-object"></a>Origine dati per un oggetto

È possibile creare un'origine dati da qualsiasi oggetto che  espone una o più proprietà pubbliche eseguendo configurazione guidata origine dati e quindi selezionando il **tipo** di origine dati Oggetto. Tutte le proprietà pubbliche di un oggetto vengono visualizzate nei **Data source** finestra. Se si usa un Entity Framework è stato generato un modello, qui è possibile trovare le classi di entità che sono le origini dati per l'applicazione.

Nella pagina **Selezione oggetti dati** espandere i nodi nella visualizzazione albero per individuare gli oggetti a cui si desidera eseguire l'associazione. La visualizzazione albero contiene nodi per il progetto e per gli assembly e altri progetti a cui fa riferimento il progetto.

Se si desidera eseguire l'associazione a un oggetto in un assembly  o in  un progetto che non viene visualizzato nella visualizzazione albero, fare clic su Aggiungi riferimento e usare la finestra di dialogo Aggiungi riferimento per aggiungere un riferimento all'assembly o al progetto. Dopo aver aggiunto il riferimento, l'assembly o il progetto viene aggiunto alla visualizzazione albero.

> [!NOTE]
> Potrebbe essere necessario compilare il progetto che contiene gli oggetti prima che gli oggetti vengano visualizzati nella visualizzazione albero.

> [!NOTE]
> Per supportare il trascinamento della data binding, gli oggetti che implementano l'interfaccia <xref:System.ComponentModel.ITypedList> o devono avere un costruttore <xref:System.ComponentModel.IListSource> predefinito. In caso Visual Studio non è possibile creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="data-source-for-a-sharepoint-list"></a>Origine dati per un elenco SharePoint

È possibile creare un'origine dati da un elenco SharePoint eseguendo **la** Configurazione guidata origine dati e selezionando il tipo di origine dati **SharePoint.** SharePoint espone i dati tramite WCF Data Services, quindi la creazione di un'origine dati SharePoint è identica alla creazione di un'origine dati da un servizio. Se si **seleziona l'elemento SharePoint** nella Configurazione guidata origine dati, viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio in** cui è possibile connettersi al servizio dati SharePoint puntando al server SharePoint.  A questo scopo è necessario SharePoint SDK.

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
