---
title: Aggiungere nuove origini dati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db550b2a99f12190cac0bde74859191c2943b2d5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102757"
---
# <a name="add-new-data-sources"></a>Aggiungere nuove origini dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel contesto di strumenti di dati .NET in Visual Studio, il termine *zdroj dat* fa riferimento a oggetti .NET che si connettono a un archivio dati e rendere disponibili i dati a un'applicazione .NET. Le finestre di progettazione di Visual Studio possono usare l'output dell'origine dati per generare il codice boilerplate che associa i dati a un form quando si trascinano gli oggetti di database dalla finestra **Data Source**. Questo tipo di origine dati può essere:  
  
- Una classe in un modello di Entity Framework che è associato a un tipo di database.  
  
- Un set di dati associato a un tipo di database.  
  
- Una classe che rappresenta un servizio di rete, ad esempio un servizio dati di Windows Communication Foundation (WCF) o un servizio REST.  
  
- Una classe che rappresenta un servizio di SharePoint.  
  
- Una classe o una raccolta nella soluzione.  
  
> [!NOTE]
>  Se non si usa funzionalità di associazione dati, set di dati, Entity Framework, LINQ to SQL, WCF o SharePoint, il concetto di "data source" non è applicabile. È sufficiente connettersi direttamente al database utilizzando gli oggetti di SQLCommand e comunicare direttamente con il database.  
  
 Per creare e modificare origini dati usando il **configurazione guidata origine dati** in un'applicazione Windows Forms o Windows Presentation Foundation. Per Entity Framework, prima di tutto creare le classi di entità e quindi avviare la procedura guidata selezionando **Project** > **Aggiungi nuova origine dati** (descritto in dettaglio più avanti in questo articolo).  
  
 ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png "configurazione guidata origine dati")  
  
 Dopo aver creato un'origine dati, viene visualizzato nei **Zdroje dat** finestra degli strumenti (Maiusc + Alt + D o **View** > **Other Windows**  >  **Zdroj dat**). È possibile trascinare un'origine dati dal **Data source** finestra in un'area di progettazione form o controllo. In questo modo, generazione del codice boilerplate, ovvero il codice che consente di visualizzare i dati che hanno origine nell'archivio dati all'utente. La figura seguente mostra un set di dati che è stato eliminato in un form di Windows. Se si seleziona F5 sull'applicazione, i dati dal database sottostante apparirebbe nei controlli del form.  
  
 ![Operazione di trascinamento Zdroj](../data-tools/media/raddata-data-source-drag-operation.png "raddata Zdroj dat operazione di trascinamento")  
  
## <a name="data-source-for-a-database-or-a-database-file"></a>Origine dati per un database o un file di database  
  
### <a name="dataset"></a>Set di dati  
 Per creare un set di dati come origine dati, eseguire la **configurazione guidata origine dati** (**Project** > **aggiungere nuovi dati** origine) e scegliere il  **Database** tipo origine dati. Seguire le istruzioni per specificare una connessione di database nuovo o esistente o un file di database.  
  
### <a name="entity-classes"></a>Classi di entità  
 Per creare un modello di Entity Framework come origine dati, eseguire prima la **Entity Data Model Wizard** per creare le classi di entità (**Project** > **Aggiungi nuovo elemento**  >  **ADO.NET Entity Data Model**).  
  
 ![Nuovo elemento di progetto di modello di Entity Framework](../data-tools/media/raddata-new-entity-framework-model-project-item.png "raddata elemento del progetto modello nuovo Entity Framework")  
  
 Scegliere il metodo mediante il quale si desidera generare il modello.  
  
 ![Procedura guidata Entity Data Model](../data-tools/media/raddata-entity-data-model-wizard.png "raddata procedura guidata Entity Data Model")  
  
 Aggiungere il modello come origine dati. Le classi che sono state generate vengono visualizzati nei **configurazione guidata origine dati** quando si sceglie il **oggetti** categoria.  
  
 ![Configurazione guidata origine dati con classi di entità](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png "raddata configurazione guidata origine dati con classi di entità")  
  
## <a name="data-source-for-a-service"></a>Origine dati per un servizio  
 Per creare un'origine dati da un servizio, eseguire la **configurazione guidata origine dati** e scegliere il **servizio** tipo origine dati. Si tratta davvero solo una scelta rapida per il **Aggiungi riferimento al servizio** nella finestra di dialogo è anche possibile accedere facendo clic con il progetto in **Esplora soluzioni** e scegliendo **Aggiungi riferimento al servizio** .  
  
 Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto. Visual Studio crea anche gli oggetti proxy che corrispondono agli oggetti restituito dal servizio. Ad esempio, un servizio che restituisce un set di dati è rappresentato nel progetto come un set di dati. un servizio che restituisce che un tipo specifico viene rappresentato nel progetto come tipo restituito.  
  
 Uno dei seguenti tipi di servizi, è possibile creare un'origine dati:  
  
- WCF Data Services. Per altre informazioni, vedere [Panoramica](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
- Servizi dati WCF. Per altre informazioni, vedere [servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
- Servizi Web.  
  
    > [!NOTE]
    >  Gli elementi visualizzati nei **Data source** finestra dipendono i dati restituiti al servizio. Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili. Ad esempio, se il servizio restituisce un set di dati non tipizzati, nessun elemento verrà visualizzato nei **Zdroje dat** finestra una volta completata la procedura guidata. Questo avviene perché DataSet non tipizzati non forniscono alcuno schema, e pertanto la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.  
  
## <a name="data-source-for-an-object"></a>Origine dati per un oggetto  
 È possibile creare un'origine dati da qualsiasi oggetto che espone uno o più proprietà pubbliche eseguendo la **configurazione guidata origine dati** e quindi selezionando il **oggetto** tipo origine dati. Tutte le proprietà pubbliche di un oggetto vengono visualizzate nei **Data source** finestra.   Se si usa Entity Framework e hanno generato un modello, si tratta in cui è trovare le classi di entità che saranno le origini dati per l'applicazione.  
  
 Nel **selezionare gli oggetti dati** , espandere i nodi nella visualizzazione albero per individuare gli oggetti che si desidera associare. Visualizzazione albero contiene nodi per il progetto e per gli assembly e altri progetti di cui vengono fatto riferimento dal progetto.  
  
 Se si desidera associare a un oggetto in un assembly o un progetto che non compare nella visualizzazione albero, fare clic su **Aggiungi riferimento** e utilizzare il **Add Reference Dialog Box** per aggiungere un riferimento al progetto o assembly. Dopo aver aggiunto il riferimento, l'assembly o il progetto viene aggiunto alla visualizzazione albero.  
  
> [!NOTE]
>  Potrebbe essere necessario compilare il progetto che contiene gli oggetti prima che gli oggetti vengono visualizzati nella visualizzazione albero.  
  
> [!NOTE]
>  Per supportare l'associazione di dati di trascinamento e rilascio, gli oggetti che implementano il <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaccia deve avere un costruttore predefinito. In caso contrario, Visual Studio non è possibile creare un'istanza di oggetto origine dati e verrà visualizzato un errore quando si trascina l'elemento all'area di progettazione.  
  
## <a name="data-source-for-a-sharepoint-list"></a>Origine dati per un elenco di SharePoint  
 È possibile creare un'origine dati da un elenco di SharePoint eseguendo il **configurazione guidata origine dati** e selezionando le **SharePoint** tipo origine dati. SharePoint espone i dati mediante [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], pertanto la creazione di un'origine dati SharePoint è analoga alla creazione di un'origine dati da un servizio. Selezionando il **SharePoint** degli elementi nella **configurazione guidata origine dati** consente di aprire il **Aggiungi riferimento al servizio** finestra di dialogo, a cui ci si connette al servizio dati di SharePoint puntando al server SharePoint.  Questa operazione richiede il SDK di SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
