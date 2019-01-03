---
title: Progettazione di un Business Data Connectivity Model | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97172f0b3a03d015c087a58077696ceff2b4369d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858383"
---
# <a name="design-a-business-data-connectivity-model"></a>Progettare un modello di integrazione applicativa dei dati business
  È possibile sviluppare un modello per il servizio di integrazione applicativa dei dati (BDC) mediante l'aggiunta di metodi e le entità in un file di modello. Un'entità descrive una raccolta di campi di dati. Ad esempio, un'entità può rappresentare una tabella in un database. Un metodo esegue un'attività, ad esempio aggiungendo, eliminando o aggiornando dati rappresentati dall'entità. Per altre informazioni, vedere [integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="add-entities"></a>Aggiungi entità
 È possibile aggiungere un'entità trascinando o copiando un **Entity** Visual Studio **della casella degli strumenti** nella finestra di progettazione integrazione applicativa dei dati. Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definire i campi dell'entità in una classe. Ad esempio, è possibile aggiungere un campo denominato `Address` a un `Customer` classe. È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata tramite altri strumenti, ad esempio il Object Relational Designer (O/R Designer). Il nome dell'entità e il nome della classe che rappresenta l'entità non è in modo che corrispondano. La classe viene correlata all'entità quando si definiscono i metodi nel modello.  
  
## <a name="add-methods"></a>Aggiungere i metodi
 Il servizio di integrazione applicativa dei dati chiama i metodi nel modello quando gli utenti di visualizzano, aggiungere, aggiornare o eliminare le informazioni in una Web Part basata sul modello o un elenco. È necessario aggiungere un metodo per il modello per ogni attività che l'utente può eseguire. Creare metodi selezionando uno dei cinque tipi di metodo di base dal **Dettagli metodo BDC** finestra. Nella tabella seguente vengono descritti i cinque metodi di base di un modello di integrazione applicativa dei dati.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Finder|Restituisce una raccolta di istanze di entità. Chiamato quando l'utente apre l'elenco o una Web Part. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md).|  
|Finder specifico|Restituisce un'istanza di entità specifico. Chiamato quando un utente visualizza i dettagli di un elemento specifico in un elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Aggiunge nuovi dati all'origine dati di un'entità. Chiamato quando gli utenti scelgono il **nuovo elemento** pulsante della barra multifunzione di un elenco che si basa sul modello. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modifica i dati in un elenco. Chiamato quando gli utenti aggiornano le informazioni in un elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Rimuove i dati. Chiamato quando gli utenti di eliminare un elemento dall'elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="define-method-parameters"></a>Definire i parametri del metodo
 Quando si crea un metodo, Visual Studio aggiunge i parametri di input e outpui appropriati per il tipo del metodo. Questi parametri sono semplicemente segnaposto. Nella maggior parte dei casi, è necessario modificare i parametri in modo da passare o restituire il tipo di dati corretto. Ad esempio, per impostazione predefinita, un metodo Finder restituisce una stringa. Nella maggior parte dei casi, si desidera modificare il parametro restituito del metodo Finder in modo che restituisca una raccolta di entità. È possibile eseguire tale operazione modifica il descrittore di tipo del parametro. Un descrittore di tipo è una raccolta di attributi che descrive il tipo di dati di un parametro. Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio consente agli utenti di copiare i descrittori di tipo tra parametri del modello. Ad esempio, è possibile definire un descrittore di tipo denominato `CustomerTD` per il parametro restituito di `GetCustomer` (metodo). È possibile copiare il `CustomerTD` nel descrittore di tipo i **Esplora integrazione applicativa dei dati**e quindi incollare tale descrittore di tipo per il parametro di input del `CreateCustomer` (metodo). Ciò impedisce all'utente di dover definire più di una volta il descrittore di tipo stesso.  
  
## <a name="method-instances"></a>Istanze (metodo)
 Quando si crea un metodo, Visual Studio aggiunge un'istanza del metodo predefinito. Un'istanza del metodo è un riferimento a un metodo con i valori predefiniti per i parametri. Un singolo metodo può avere più istanze di metodo. Ogni istanza è una combinazione di firma del metodo e un set di valori predefiniti. Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Quando si esegue il progetto, le istanze di metodo vengono visualizzate in un elenco di riepilogo a discesa sopra l'elenco di SharePoint. Gli utenti possono scegliere istanze del metodo per visualizzare i dati.  
  
 Per aggiungere i valori predefiniti per l'istanza del metodo, è necessario modificare direttamente il codice XML del modello. Per altre informazioni, vedere [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="add-filter-descriptors"></a>Aggiungere i descrittori di filtro
 I consumer del modello potrebbe essere necessario recuperare le istanze di un'entità che corrispondono a certi criteri. Per abilitare questa funzionalità, è possibile aggiungere un descrittore di filtro a un metodo. Descrittori di filtro consentono ai consumer del modello filtrare il set di risultati di metodo passando i valori per i metodi prima che vengano eseguiti. Per altre informazioni, vedere [Procedura: Aggiungere i parametri di filtro alle operazioni per limitare le istanze dal sistema esterno](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint fornisce diverse funzionalità che consentono agli utenti di fornire i valori di filtro. Web part dei dati di Business, ad esempio, fornire una casella di testo filtro. Gli utenti possono limitare i dati in un elenco immettendo un valore nella casella di testo. Per altre informazioni su come aggiungere un descrittore di filtro a un metodo, vedere [come: Aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Proprietà del descrittore di filtro
 È necessario impostare il valore della **descrittore di tipi associato**, **nome**, e **tipo** le proprietà di un descrittore di filtro. Tutte le altre proprietà sono facoltative.  
  
 Il **descrittori di tipo associati** proprietà si riferisce il descrittore di filtro per un parametro di input. Quando un utente fornisce un valore di filtro, il servizio di integrazione applicativa dei dati passa tale valore al metodo usando il parametro di input.  
  
 Il **tipo** proprietà descrive il criterio di filtro che si desidera utilizzare. In SharePoint, il criterio di filtro selezionato interessa il testo visualizzato nell'interfaccia utente (UI). Ad esempio, per un criterio di filtro di criterio di confronto, il testo **è uguale a** viene visualizzato come un controllo di sopra di una Web Part dei dati aziendali. Per altre informazioni su ogni modello di filtro, vedere [tipi di filtri supportati per l'integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Per altre informazioni sulle proprietà di un descrittore di filtro, vedere [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="provide-default-values"></a>Fornire valori predefiniti
 In alcuni casi, l'utente potrebbe non fornire un valore di filtro. È possibile fornire un valore predefinito mediante l'aggiunta di un valore predefinito per l'istanza del metodo oppure impostando il valore predefinito nel codice del metodo. Per altre informazioni su come aggiungere un valore predefinito per l'istanza del metodo, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Per un esempio di come impostare il valore predefinito di un parametro di input nel codice del metodo, vedere [come: Aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validate-the-model"></a>Convalidare il modello
 È possibile convalidare il modello durante lo sviluppo. Visual Studio identifica i problemi che impediscono il modello si comporta come previsto. Questi problemi vengono visualizzati in Visual Studio **elenco errori**.  
  
 È possibile convalidare un modello aprendo il menu di scelta rapida per la finestra di progettazione di integrazione applicativa dei dati e quindi scegliendo **Validate**. Se il modello contiene eventuali errori, vengono visualizzati nei **elenco errori**. È possibile spostare rapidamente il cursore sul codice contenente un errore facendo doppio clic sull'errore nell'elenco. In alternativa, è possibile scegliere il **F8** oppure **MAIUSC**+**F8** chiavi ripetutamente per spostarsi avanti o indietro negli errori nell'elenco.  
  
 Quando le regole del modello vengono violate in qualche modo, possono verificarsi errori di convalida. Ad esempio, se il **IsCollection** proprietà di un descrittore di tipo è impostata su **true**, ma non descrittori di tipo figlio esistono, verrà visualizzato un errore di convalida. Potrebbe essere necessario fare riferimento alle regole di un modello di integrazione applicativa dei dati per comprendere alcuni errori che vengono visualizzati in Visual Studio **elenco errori**. Per altre informazioni sulle regole di un modello di integrazione applicativa dei dati, vedere [Schema di BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debug-the-solution-that-contains-the-model"></a>Il debug della soluzione che contiene il modello
 Come per qualsiasi codice in Visual Studio, è possibile eseguire il debug del codice. Per eseguire il debug del codice, impostare i punti di interruzione in qualsiasi punto nel codice e quindi avviare il debugger. Visual Studio apre il sito di SharePoint. In SharePoint, creare un elenco o una Web Part che utilizza i dati aziendali. Quindi, è possibile esaminare il codice. Per altre informazioni sul debug di progetti SharePoint, vedere [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 È anche possibile eseguire il debug di codice negli assembly personalizzati che aggiungono al progetto. Tuttavia, per eseguire il debug di codice in un assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, vedere [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per altre informazioni sull'aggiunta di un assembly personalizzato al progetto, vedere [come: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configure-bdc-security"></a>Configurare la sicurezza di integrazione applicativa dei dati
 Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint, è possibile eseguire il debug, la soluzione. Per modificare queste impostazioni, aprire l'applicazione di servizio Business Data Connectivity nel sito Web di SharePoint 2010 Central Administration. Nel **impostare le autorizzazioni di Store metadati** nella finestra di dialogo Aggiungi account utente e quindi selezionare una delle opzioni seguenti:  
  
|Attività|Opzione|  
|----------|------------|  
|Per distribuire i modelli per il servizio di integrazione applicativa dei dati.|Edit|  
|Per creare elenchi e le Web part tramite esterno tipi di contenuto (entità) nel modello.|Selezione nei client|  
|Per creare, leggere, aggiornare ed eliminare dati di entità.|Esegui|  
  
 Per altre informazioni su queste impostazioni, vedere [gestione dei servizi di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 È anche possibile impostare le autorizzazioni di sicurezza per singoli modelli o tipi di contenuto esterno. Per altre informazioni su come impostare le autorizzazioni di sicurezza di un modello, vedere [modelli BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Per altre informazioni su come impostare le autorizzazioni di sicurezza di un tipo di contenuto esterno, vedere [gestione dei tipi di contenuto esterno](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Usare queste impostazioni per il debug di una soluzione nel SharePoint Server locale. Per altre informazioni su come configurare le impostazioni di sicurezza relative all'integrazione applicativa dei dati nel server di produzione SharePoint, vedere [Cenni preliminari sulla sicurezza di servizi di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retract-models-that-become-corrupt"></a>Ritirare i modelli di stati danneggiati
 Quando il debugger viene avviato per la prima volta, in Visual Studio l'intero modello viene distribuito in SharePoint. Per ogni momento successivo, Visual Studio aggiorna il modello in SharePoint con tutte le modifiche apportate tra le distribuzioni.  
  
 Potrebbero esserci situazioni in cui si desidera che Visual Studio per il ritiro completamente il modello da SharePoint. Ad esempio, un modello potrebbe essere danneggiato.  Per ridistribuire il modello in SharePoint, impostare il **aggiornamento incrementale** proprietà del modello da **False**, e quindi avviare il debugger. Il **aggiornamento incrementale** proprietà viene visualizzata nella **delle proprietà** finestra quando si seleziona il nodo che rappresenta il modello nel **Esplora integrazione applicativa dei dati**. Per impostazione predefinita, il nome del modello è **BdcModel1**.  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>Modificare i nomi degli identificatori di entità nel modello
 Se si modifica il nome di un identificatore dopo avere distribuito il modello, è possibile ricevere un errore di distribuzione. Non è possibile risolvere questo errore impostando il **aggiornamento incrementale** proprietà del modello da **False**. È necessario recuperare manualmente il modello e quindi distribuire nuovamente la soluzione. Per altre informazioni, vedere [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md). È possibile evitare questo errore impostando il **aggiornamento incrementale** proprietà **False** prima che si distribuisce il modello.  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>Individua la documentazione per gli elementi del modello di integrazione applicativa dei dati
 Visual Studio aggiunge un elemento XML per il modello per ogni entità, metodo o un altro elemento creato. Attributi dell'elemento visualizzati come proprietà nella **proprietà** finestra. Per informazioni sugli elementi e attributi generato da Visual Studio quando si progetta il modello, vedere [Schema di BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Argomenti correlati
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Panoramica degli strumenti di progettazione modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)|Vengono descritti gli strumenti che è possibile utilizzare per progettare visivamente un modello per l'integrazione applicativa dei dati.|  
|[Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)|Illustra come aggiungere tipi di contenuto esterno, o entità, al modello.|  
|[Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)|Illustra come aggiungere un metodo che consente agli utenti di visualizzare un elenco di entità in un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)|Illustra come aggiungere un metodo che consente agli utenti di visualizzare i dettagli di un'entità specifica.|  
|[Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)|Illustra come aggiungere un metodo che consente agli utenti di aggiungere record a un'origine dati direttamente da un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Illustra come aggiungere un metodo che consente agli utenti di rimuovere i dati da un'origine dati utilizzando le opzioni di interfaccia utente (UI) di un elenco o una Web Part.|  
|[Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)|Illustra come aggiungere un metodo che consente agli utenti di modificare i record di dati in un'origine dati direttamente da un elenco o una Web Part.|  
|[Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Illustra come usare la finestra dei dettagli del metodo in Visual Studio per aggiungere parametri di input e restituiti a un metodo.|  
|[Procedura: Definire il descrittore di tipo di parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Illustra come definire i tipi di dati di parametro nel modello.|  
|[Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)|Illustra come creare un'istanza di un metodo che esegue l'integrazione applicativa dei dati.|  
|[Procedura: Aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Illustra come consentire agli utenti di limitare il numero di istanze restituite da un metodo Finder.|  
|[Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)|Viene descritto come definire le relazioni tra entità nel modello. Web part dei dati di business, gli elenchi esterni e applicazioni personalizzate è possono visualizzare tali relazioni tra i dati in un'interfaccia utente (UI).|  
|[Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)|Illustra come definire le relazioni tra entità nel modello.|  
|[Procedura dettagliata: Creare un elenco esterno in SharePoint utilizzando i dati di business](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Vengono fornite istruzioni dettagliate che illustrano come creare e testare un modello che consente di visualizzare i contatti in un elenco esterno di SharePoint.|  
|[Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Viene fornita una panoramica della creazione e la progettazione di modelli per il servizio di integrazione applicativa dei dati.|  
