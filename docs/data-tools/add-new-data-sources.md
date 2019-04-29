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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 05a07fc3cb72f923d28ff907c9aec69620cbd40d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824888"
---
# <a name="add-new-data-sources"></a>Aggiungere nuove origini dati

Nel contesto di strumenti di dati .NET in Visual Studio, il termine *data source* fa riferimento a oggetti .NET che si connettono a un archivio dati e rendere i dati disponibili a un'applicazione .NET. Le finestre di progettazione di Visual Studio possono usare l'output dell'origine dati per generare il codice boilerplate che associa i dati a un form quando si trascinano gli oggetti di database dalla finestra **Data Source**. Questo tipo di origine dati può essere:

- Una classe in un modello di Entity Framework che è associato a un tipo di database.

- Un set di dati associato a un tipo di database.

- Una classe che rappresenta un servizio di rete, ad esempio un servizio dati di Windows Communication Foundation (WCF) o un servizio REST.

- Una classe che rappresenta un servizio di SharePoint.

- Una classe o una raccolta nella soluzione.

> [!NOTE]
> Se non si usa funzionalità di associazione dati, set di dati, Entity Framework, LINQ to SQL, WCF o SharePoint, il concetto di "data source" non è applicabile. È sufficiente connettersi direttamente al database utilizzando gli oggetti di SQLCommand e comunicare direttamente con il database.

Per creare e modificare origini dati usando il **configurazione guidata origine dati** in un'applicazione Windows Forms o Windows Presentation Foundation. Per Entity Framework, prima di tutto creare le classi di entità e quindi avviare la procedura guidata selezionando **Project** > **Aggiungi nuova origine dati** (descritto in dettaglio più avanti in questo articolo).

![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>Finestra Origini dati

Dopo aver creato un'origine dati, viene visualizzato nei **Data source** finestra degli strumenti.

> [!TIP]
> Per aprire la finestra **Data source**, assicurarsi che il progetto sia aperto e quindi premere **MAIUSC**+**Alt**+**1!d**oppure scegliere **View** > **Other Windows** > **Data source**.

È possibile trascinare un'origine dati dal **Data source** finestra in un'area di progettazione form o controllo. In questo modo boilerplate generazione del codice che consente di visualizzare i dati dall'archivio dati.

La figura seguente mostra un set di dati che è stato eliminato in un form di Windows. Se si seleziona **F5** nell'applicazione, i dati dal database sottostante vengono visualizzati nei controlli del form.

![Operazione di trascinamento sull'origine dati](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>Origine dati per un database o un file di database

È possibile creare un set di dati o un modello di Entity Framework da utilizzare come origine dati per un database o un file di database.

### <a name="dataset"></a>Set di dati

Per creare un set di dati come origine dati, eseguire la **configurazione guidata origine dati** selezionando **Project** > **Aggiungi nuova origine dati**. Scegliere il **Database** dell'origine dati digitare e seguire le istruzioni per specificare una connessione di database nuovo o esistente o un file di database.

### <a name="entity-classes"></a>Classi di entità

Per creare un modello Entity Framework come origine dati:

1. Eseguire la **procedura guidata Entity Data Model** per creare le classi di entità. Selezionare **Project** > **Aggiungi nuovo elemento** > **ADO.NET Entity Data Model**.

   ![Nuovo elemento di progetto di modello di Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. Scegliere il metodo che si desidera generare il modello da.

   ![Entity Data Model (procedura guidata)](../data-tools/media/raddata-entity-data-model-wizard.png)

1. Aggiungere il modello come origine dati. Le classi generate vengono visualizzati nei **configurazione guidata origine dati** quando si sceglie il **oggetti** categoria.

   ![Configurazione guidata origine dati con classi di entità](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>Origine dati per un servizio

Per creare un'origine dati da un servizio, eseguire la **configurazione guidata origine dati** e scegliere il **servizio** tipo origine dati. Questo è solo una scorciatoia per la **Aggiungi riferimento al servizio** nella finestra di dialogo è anche possibile accedere facendo clic con il progetto in **Esplora soluzioni** e scegliendo **Aggiungi riferimento al servizio**.

Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto. Visual Studio crea anche gli oggetti proxy che corrispondono agli oggetti restituito dal servizio. Ad esempio, un servizio che restituisce un set di dati è rappresentato nel progetto come un set di dati. un servizio che restituisce che un tipo specifico viene rappresentato nel progetto come tipo restituito.

Uno dei seguenti tipi di servizi, è possibile creare un'origine dati:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [Servizi WCF](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- Servizi Web

    > [!NOTE]
    > Gli elementi visualizzati nei **Data source** finestra dipendono i dati restituiti al servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, viene visualizzato alcun elemento nel **Data source** finestra una volta completata la procedura guidata. Questo avviene perché DataSet non tipizzati non forniscono alcuno schema, e pertanto la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.

## <a name="data-source-for-an-object"></a>Origine dati per un oggetto

È possibile creare un'origine dati da qualsiasi oggetto che espone uno o più proprietà pubbliche eseguendo la **configurazione guidata origine dati** e quindi selezionando il **oggetto** tipo origine dati. Tutte le proprietà pubbliche di un oggetto vengono visualizzate nei **Data source** finestra. Se si usa Entity Framework e hanno generato un modello, si tratta in cui è trovare le classi di entità che sono le origini dati per l'applicazione.

Nel **selezionare gli oggetti dati** , espandere i nodi nella visualizzazione albero per individuare gli oggetti che si desidera associare. Visualizzazione albero contiene nodi per il progetto e per gli assembly e altri progetti di cui vengono fatto riferimento dal progetto.

Se si desidera associare a un oggetto in un assembly o un progetto che non compare nella visualizzazione albero, fare clic su **Aggiungi riferimento** e utilizzare il **Add Reference Dialog Box** per aggiungere un riferimento al progetto o assembly. Dopo aver aggiunto il riferimento, l'assembly o il progetto viene aggiunto alla visualizzazione albero.

> [!NOTE]
> Potrebbe essere necessario compilare il progetto che contiene gli oggetti prima che gli oggetti vengono visualizzati nella visualizzazione albero.

> [!NOTE]
> Per supportare l'associazione di dati di trascinamento e rilascio, gli oggetti che implementano il <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaccia deve avere un costruttore predefinito. In caso contrario, Visual Studio non è possibile creare un'istanza di oggetto origine dati e visualizza un errore quando si trascina l'elemento all'area di progettazione.

## <a name="data-source-for-a-sharepoint-list"></a>Origine dati per un elenco di SharePoint

È possibile creare un'origine dati da un elenco di SharePoint eseguendo il **configurazione guidata origine dati** e selezionando le **SharePoint** tipo origine dati. SharePoint espone i dati tramite WCF Data Services, pertanto la creazione di un'origine dati SharePoint è analoga alla creazione di un'origine dati da un servizio. Selezionando il **SharePoint** degli elementi nella **configurazione guidata origine dati** consente di aprire il **Aggiungi riferimento al servizio** finestra di dialogo, a cui ci si connette al servizio dati di SharePoint puntando al server SharePoint. Questa operazione richiede il SDK di SharePoint.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
