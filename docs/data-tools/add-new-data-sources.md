---
title: Aggiungere nuove origini dati
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 555d32eb295e944060d2efe0b843e9d157b7c675
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302252"
---
# <a name="add-new-data-sources"></a>Aggiungere nuove origini dati

Nel contesto di strumenti di dati .NET in Visual Studio, il termine *data source* fa riferimento a oggetti .NET che si connettono a un archivio dati e rendere i dati disponibili a un'applicazione .NET. Le finestre di progettazione di Visual Studio possono usare l'output dell'origine dati per generare il codice boilerplate che associa i dati a un form quando si trascinano gli oggetti di database dalla finestra **Data Source**. Questo tipo di origine dati può essere:

- Classe in un modello Entity Framework associato a un tipo di database.

- Set di dati associato a un tipo di database.

- Classe che rappresenta un servizio di rete, ad esempio un servizio dati Windows Communication Foundation (WCF) o un servizio REST.

- Classe che rappresenta un servizio di SharePoint.

- Classe o raccolta nella soluzione.

> [!NOTE]
> Se non si utilizzano funzionalità di associazione dati, set di dati, Entity Framework, LINQ to SQL, WCF o SharePoint, il concetto di "origine dati" non è applicabile. È sufficiente connettersi direttamente al database utilizzando gli oggetti SQLCommand e comunicare direttamente con il database.

È possibile creare e modificare le origini dati utilizzando la **Configurazione guidata origine dati** in un'applicazione Windows Form o Windows Presentation Foundation. Per Entity Framework, creare innanzitutto le classi di entità, quindi avviare la procedura guidata selezionando **Aggiungi** > **nuova origine dati** (descritta più dettagliatamente più avanti in questo articolo).

![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Finestra Origini dati

Dopo aver creato un'origine dati, viene visualizzato nei **Data source** finestra degli strumenti.

> [!TIP]
> Per aprire la finestra **Data source**, assicurarsi che il progetto sia aperto e quindi premere **MAIUSC**+**Alt**+**1!d**oppure scegliere **View** > **Other Windows** > **Data source**.

È possibile trascinare un'origine dati dal **Data source** finestra in un'area di progettazione form o controllo. In questo modo viene generato codice boilerplate che visualizza i dati dall'archivio dati.

Nella figura seguente viene illustrato un set di dati che è stato rilasciato in un Windows Form.The following illustration shows a dataset that has been dropped onto a Windows form. Se si seleziona **F5** nell'applicazione, i dati del database sottostante vengono visualizzati nei controlli del form.

![Operazione di trascinamento dell'origine datiData Source drag operation](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origine dati per un database o un file di databaseData source for a database or a database file

È possibile creare un set di dati o un modello Entity Framework da utilizzare come origine dati per un database o un file di database.

### <a name="dataset"></a>Set di dati

Per creare un dataset come origine dati, eseguire la **Configurazione guidata origine** dati selezionando Aggiungi **progetto** > **nuova origine dati**. Scegliere il tipo di origine dati **Database** e seguire le istruzioni visualizzate per specificare una connessione di database nuova o esistente oppure un file di database.

### <a name="entity-classes"></a>Classi di entità

Per creare un modello Entity Framework come origine dati:

1. Eseguire la **procedura guidata Entity Data Model** per creare le classi di entità. Selezionare **Aggiunta** > **progetto nuovo elemento** > **ADO.NET Entity Data Model**.

   ![Nuovo elemento di progetto del modello Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Scegliere il metodo in base al quale si desidera generare il modello.

   ![Entity Data Model (procedura guidata)](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Aggiungere il modello come origine dati. Le classi generate vengono visualizzate nella **Configurazione guidata origine dati** quando si sceglie la categoria **Oggetti.**

   ![Configurazione guidata origine dati con classi di entitàData Source Configuration Wizard with Entity Classes](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origine dati per un servizioData source for a service

Per creare un'origine dati da un servizio, eseguire la Configurazione guidata origine dati e scegliere il tipo di origine dati Servizio.To create a data source from a **service,** run the Data Source Configuration Wizard and choose the **Service** data-source type. Si tratta solo di un collegamento alla finestra di dialogo **Aggiungi riferimento** al servizio , a cui è possibile accedere anche facendo clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e selezionando Aggiungi riferimento al **servizio**.

Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto. Visual Studio crea anche oggetti proxy che corrispondono agli oggetti restituiti dal servizio. Ad esempio, un servizio che restituisce un set di dati viene rappresentato nel progetto come set di dati. un servizio che restituisce un tipo specifico è rappresentato nel progetto come il tipo restituito.

È possibile creare un'origine dati dai seguenti tipi di servizi:

- [Servizi dati WCFWCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servizi WCFWCF services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- SERVIZI WEB

    > [!NOTE]
    > Gli elementi visualizzati nei **Data source** finestra dipendono i dati restituiti al servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, viene visualizzato alcun elemento nel **Data source** finestra una volta completata la procedura guidata. Ciò è dovuto al fatto che i dataset non tipizzati non forniscono uno schema e pertanto la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

## <a name="data-source-for-an-object"></a>Origine dati per un oggettoData source for an object

È possibile creare un'origine dati da qualsiasi oggetto che espone una o più proprietà pubbliche eseguendo la **Configurazione guidata origine dati** e selezionando il tipo di origine dati **Oggetto.** Tutte le proprietà pubbliche di un oggetto vengono visualizzate nei **Data source** finestra. Se si usa Entity Framework e si è generato un modello, è qui che si trovano le classi di entità che sono le origini dati per l'applicazione.

Nella pagina **Selezione oggetti dati** espandere i nodi nella visualizzazione struttura ad albero per individuare gli oggetti a cui si desidera eseguire l'associazione. La visualizzazione struttura ad albero contiene nodi per il progetto e per gli assembly e altri progetti a cui fa riferimento il progetto.

Se si desidera eseguire l'associazione a un oggetto in un assembly o in un progetto che non viene visualizzato nella visualizzazione struttura ad albero, fare clic su **Aggiungi riferimento** e utilizzare la finestra di **dialogo Aggiungi riferimento** per aggiungere un riferimento all'assembly o al progetto. Dopo aver aggiunto il riferimento, l'assembly o il progetto viene aggiunto alla vista ad albero.

> [!NOTE]
> Potrebbe essere necessario compilare il progetto che contiene gli oggetti prima che gli oggetti vengano visualizzati nella visualizzazione struttura ad albero.

> [!NOTE]
> Per supportare l'associazione dati di <xref:System.ComponentModel.ITypedList> trascinamento della selezione, gli oggetti che implementano l'interfaccia o <xref:System.ComponentModel.IListSource> devono avere un costruttore predefinito. In caso contrario, Visual Studio non è possibile creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="data-source-for-a-sharepoint-list"></a>Origine dati per un elenco di SharePointData source for a SharePoint list

È possibile creare un'origine dati da un elenco SharePoint eseguendo la Configurazione guidata origine dati e selezionando il tipo di origine dati di SharePoint.You can create a data source from a SharePoint list by running the **Data Source Configuration Wizard** and selecting the **SharePoint** data-source type. SharePoint espone i dati tramite WCF Data ServicesWCF Data Services, pertanto la creazione di un'origine dati di SharePoint equivale alla creazione di un'origine dati da un servizio. Se si seleziona l'elemento **di SharePoint** nella **Configurazione guidata origine dati,** verrà visualizzata la finestra di dialogo Aggiungi riferimento al **servizio,** in cui ci si connette al servizio dati di SharePoint puntando al server SharePoint. Ciò richiede SharePoint SDK.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
