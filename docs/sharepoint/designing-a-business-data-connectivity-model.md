---
title: Progettazione di un modello di connettività dei dati | Microsoft Docs
description: Progettare un modello di connettività dei dati business (BDC). Aggiungere entità e metodi. Definire i parametri del metodo. Aggiungere descrittori di filtro. Convalidare il modello BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 831fe9dfe29744a395dc07a7c3d2d0ac901a43ab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628217"
---
# <a name="design-a-business-data-connectivity-model"></a>Progettare un modello di connettività dei dati aziendali
  È possibile sviluppare un modello per il servizio BDC (Business Data Connectivity) aggiungendo entità e metodi a un file di modello. Un'entità descrive una raccolta di campi dati. Ad esempio, un'entità può rappresentare una tabella in un database. Un metodo esegue un'attività, ad esempio l'aggiunta, l'eliminazione o l'aggiornamento dei dati rappresentati dalle entità. Per altre informazioni, vedere [Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Aggiungi entità
 È possibile aggiungere un'entità  trascinando o copiando un'entità dalla Visual Studio **casella** degli strumenti in Progettazione integrazione applicativa dei dati. Per altre informazioni, vedere [Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definire i campi dell'entità in una classe. Ad esempio, è possibile aggiungere un campo `Address` denominato a una classe `Customer` . È possibile aggiungere una nuova classe al progetto o usare una classe esistente creata usando altri strumenti, ad esempio Object Relational Designer (Progettazione O/R). Il nome dell'entità e il nome della classe che rappresenta l'entità non devono corrispondere. La classe viene correlata all'entità quando si definiscono i metodi nel modello.

## <a name="add-methods"></a>Aggiungere metodi
 Il servizio BDC chiama i metodi nel modello quando gli utenti visualizzano, aggiungono, aggiornano o eliminano informazioni in un elenco o in una web part basata sul modello. È necessario aggiungere un metodo al modello per ogni attività che l'utente può eseguire. Creare metodi selezionando uno dei cinque tipi di metodo di base dalla finestra **Dettagli metodo BDC.** Nella tabella seguente vengono descritti i cinque metodi di base di un modello BDC.

|Metodo|Descrizione|
|------------|-----------------|
|Finder|Restituisce una raccolta di istanze di entità. Chiamato quando l'utente apre l'elenco o la web part. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md).|
|Finder specifico|Restituisce un'istanza di entità specifica. Chiamato quando un utente visualizza i dettagli di un elemento specifico in un elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Finder specifico.](../sharepoint/how-to-add-a-specific-finder-method.md)|
|Autore|Aggiunge nuovi dati all'origine dati di un'entità. Chiamato quando gli utenti scelgono **il pulsante Nuovo** elemento sulla barra multifunzione di un elenco basato sul modello. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Modifica i dati in un elenco. Chiamato quando gli utenti aggiornano le informazioni in un elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Rimuove i dati. Chiamato quando gli utenti eliminano un elemento dall'elenco. Per altre informazioni, vedere [Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definire i parametri del metodo
 Quando si crea un metodo, Visual Studio i parametri di input e di output appropriati per il tipo di metodo. Questi parametri sono solo segnaposto. Nella maggior parte dei casi, è necessario modificare i parametri in modo che passino o restituiranno il tipo corretto di dati. Ad esempio, per impostazione predefinita, un metodo Finder restituisce una stringa. Nella maggior parte dei casi, si vuole modificare il parametro restituito del metodo Finder in modo che restituisca una raccolta di entità. A tale scopo, modificare il descrittore di tipo del parametro . Un descrittore di tipo è una raccolta di attributi che descrive il tipo di dati di un parametro. Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio consente di copiare i descrittori di tipo tra i parametri nel modello. Ad esempio, è possibile definire un descrittore di tipo denominato `CustomerTD` per il parametro restituito del metodo `GetCustomer` . È possibile copiare il descrittore di tipo in BDC Explorer e quindi incollarlo nel parametro `CustomerTD` di input del  `CreateCustomer` metodo. In questo modo non è necessario definire più volte lo stesso descrittore di tipo.

## <a name="method-instances"></a>Istanze del metodo
 Quando si crea un metodo, Visual Studio un'istanza del metodo predefinita. Un'istanza del metodo è un riferimento a un metodo, oltre ai valori predefiniti per i parametri. Un singolo metodo può avere più istanze di metodo. Ogni istanza è una combinazione della firma del metodo e di un set di valori predefiniti. Per altre informazioni, vedere [Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Quando si esegue il progetto, le istanze del metodo vengono visualizzate in un elenco a discesa sopra l'SharePoint. Gli utenti possono scegliere istanze del metodo per visualizzare i dati.

 Per aggiungere valori predefiniti all'istanza del metodo, è necessario modificare direttamente il codice XML del modello. Per altre informazioni, vedere [DefaultValue.](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14))

## <a name="add-filter-descriptors"></a>Aggiungere descrittori di filtro
 I consumer del modello potrebbero voler recuperare istanze di un'entità che soddisfano alcuni criteri. Per abilitare questa funzionalità, è possibile aggiungere un descrittore di filtro a un metodo. I descrittori di filtro consentono ai consumer del modello di filtrare i set di risultati dei metodi passando i valori ai metodi prima dell'esecuzione. Per altre informazioni, vedere [Procedura: Aggiungere parametri di filtro alle operazioni per limitare le istanze dal sistema esterno.](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14))

 SharePoint offre diverse funzionalità che consentono agli utenti di fornire valori di filtro. Ad esempio, i dati aziendali Web part una casella di testo del filtro. Gli utenti possono limitare i dati in un elenco immettendo un valore nella casella di testo. Per altre informazioni su come aggiungere un descrittore di filtro a un metodo, vedere [Procedura: Aggiungere](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)un descrittore di filtro a un metodo Finder .

### <a name="filter-descriptor-properties"></a>Proprietà del descrittore di filtro
 È necessario impostare il valore delle proprietà **Associated Type Descriptor**, **Name** **e Type** di un descrittore di filtro. Tutte le altre proprietà sono facoltative.

 La **proprietà Descrittore del tipo** associato mette in relazione il descrittore di filtro con un parametro di input. Quando un utente fornisce un valore di filtro, il servizio BDC passa tale valore al metodo usando il parametro di input .

 La **proprietà Type** descrive il criterio di filtro che si vuole usare. In SharePoint, il criterio di filtro selezionato influisce sul testo visualizzato nell'Interfaccia utente (interfaccia utente). Ad esempio, per un criterio di  filtro Comparator, il testo è uguale a viene visualizzato come controllo sopra una web part dati business. Per altre informazioni su ogni criterio di filtro, vedere [Tipi di filtri supportati dal BDC.](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))

 Per altre informazioni sulle proprietà di un descrittore di filtro, vedere [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Specificare valori predefiniti
 In alcuni casi, l'utente potrebbe non fornire un valore di filtro. È possibile specificare un valore predefinito aggiungendo un valore predefinito all'istanza del metodo o impostando il valore predefinito nel codice del metodo. Per altre informazioni su come aggiungere un valore predefinito all'istanza del metodo, vedere [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Per un esempio di come impostare il valore predefinito di un parametro di input nel codice del metodo, vedere [Procedura: Aggiungere](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)un descrittore di filtro a un metodo Finder .

## <a name="validate-the-model"></a>Convalidare il modello
 È possibile convalidare il modello durante lo sviluppo. Visual Studio identifica i problemi che possono impedire il comportamento del modello come previsto. Questi problemi vengono visualizzati nell'Visual Studio **degli errori.**

 È possibile convalidare un modello aprendo il menu di scelta rapida per Progettazione integrazione applicativa dei dati e quindi scegliendo **Convalida**. Se il modello contiene errori, vengono visualizzati **nell'Elenco errori**. È possibile spostare rapidamente il cursore sul codice contenente un errore facendo doppio clic sull'errore nell'elenco. In alternativa, è possibile premere  **ripetutamente F8** o MAIUSC F8 per spostarsi avanti o indietro tra gli +  errori nell'elenco.

 Gli errori di convalida possono verificarsi quando le regole del modello vengono violate in qualche modo. Ad esempio, se la **proprietà IsCollection** di un descrittore di tipo è impostata su **true**, ma non esistono descrittori di tipo figlio, verrà visualizzato un errore di convalida. Potrebbe essere necessario fare riferimento alle regole di un modello di integrazione applicativa dei dati per comprendere alcuni errori visualizzati nell'elenco Visual Studio **errori .** Per altre informazioni sulle regole di un modello BDC, vedere [Schema BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Eseguire il debug della soluzione che contiene il modello
 È possibile eseguire il debug del codice come si esegue il debug di qualsiasi codice in Visual Studio. Per eseguire il debug del codice, impostare punti di interruzione in qualsiasi punto del codice e quindi avviare il debugger. Visual Studio apre il SharePoint di lavoro. In SharePoint creare un elenco o una web part che usa i dati aziendali. È quindi possibile eseguire il codice un'istruzione alla volta. Per altre informazioni sul debug dei SharePoint, vedere [Risolvere i problemi relativi SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

 È anche possibile eseguire il debug del codice negli assembly personalizzati aggiunti al progetto. Tuttavia, per eseguire il debug del codice in un assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, [vedere Procedura: Aggiungere e rimuovere assembly aggiuntivi.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

 Per altre informazioni sull'aggiunta di un assembly personalizzato al progetto, vedere Procedura: Includere un assembly personalizzato in una [funzionalità BDC.](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)

### <a name="configure-bdc-security"></a>Configurare la sicurezza del BDC
 Potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint possibile eseguire il debug della soluzione. Per modificare queste impostazioni, aprire l'applicazione del servizio di connettività dei dati di business SharePoint sito Web Amministrazione centrale di SharePoint 2010. Nella finestra **di dialogo Imposta autorizzazioni archivio** metadati aggiungere l'account utente e quindi selezionare una delle opzioni seguenti:

|Attività|Opzione|
|----------|------------|
|Per distribuire modelli nel servizio BDC.|Modifica|
|Per creare elenchi e Web part usando tipi di contenuto esterni (entità) nel modello.|Selezionabile nei client|
|Per creare, leggere, aggiornare ed eliminare i dati dell'entità.|Execute|

 Per altre informazioni su queste impostazioni, vedere [Gestione del servizio di connettività dei dati di business.](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14))

 È anche possibile impostare autorizzazioni di sicurezza per singoli modelli o tipi di contenuto esterni. Per altre informazioni su come impostare le autorizzazioni di sicurezza di un modello, vedere [BDC model management](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Per altre informazioni su come impostare le autorizzazioni di sicurezza di un tipo di contenuto esterno, vedere [Gestione dei tipi di contenuto esterni.](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14))

> [!NOTE]
> Usare queste impostazioni per eseguire il debug di una soluzione nel server SharePoint Locale. Per altre informazioni su come configurare le impostazioni di sicurezza correlate al BDC nel server di SharePoint di produzione, vedere Panoramica della sicurezza di Servizi di connettività dei dati [di business.](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14))

### <a name="retract-models-that-become-corrupt"></a>Ritirare i modelli danneggiati
 Quando il debugger viene avviato per la prima volta, in Visual Studio l'intero modello viene distribuito in SharePoint. Per ogni volta che successivamente, Visual Studio il modello in SharePoint con eventuali modifiche apportate tra le distribuzioni.

 In alcune situazioni potrebbe essere necessario Visual Studio ritrarre completamente il SharePoint modello. Ad esempio, un modello potrebbe risultare danneggiato.  Per ridistribuire il modello SharePoint, impostare la proprietà **Aggiornamento incrementale** del modello su **False** e quindi avviare il debugger. La **proprietà Aggiornamento** incrementale viene visualizzata nella **finestra** Proprietà quando si seleziona il nodo che rappresenta il modello in **BDC Explorer.** Per impostazione predefinita, il nome del modello è **BdcModel1.**

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modificare i nomi degli identificatori delle entità nel modello
 Se si modifica il nome di un identificatore dopo la distribuzione del modello, è possibile che venga visualizzato un errore di distribuzione. Non è possibile risolvere questo errore impostando la **proprietà Aggiornamento** incrementale del modello su **False.** È necessario ritirare manualmente il modello e quindi distribuire nuovamente la soluzione. Per altre informazioni, vedere Risolvere [i problemi SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md). È possibile evitare questo errore impostando la proprietà **Aggiornamento incrementale** su **False** prima di distribuire inizialmente il modello.

## <a name="locate-documentation-for-bdc-model-elements"></a>Individuare la documentazione per gli elementi del modello BDC
 Visual Studio aggiunge un elemento XML al modello per ogni entità, metodo o altro elemento creato. Gli attributi degli elementi vengono visualizzati come proprietà nella **finestra** Proprietà. Per informazioni sugli elementi e gli attributi generati Visual Studio durante la progettazione del modello, vedere [Schema BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Panoramica degli strumenti di progettazione del modello BDC](../sharepoint/bdc-model-design-tools-overview.md)|Vengono descritti gli strumenti che è possibile utilizzare per progettare visivamente un modello per il BDC.|
|[Procedura: Aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)|Illustra come aggiungere tipi di contenuto esterni, o entità, al modello.|
|[Procedura: Aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)|Illustra come aggiungere un metodo che consente agli utenti di visualizzare un elenco di entità in un elenco o in una web part.|
|[Procedura: Aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)|Illustra come aggiungere un metodo che consente agli utenti di visualizzare i dettagli di un'entità specifica.|
|[Procedura: Aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di aggiungere record a un'origine dati direttamente da un elenco o da una web part.|
|[Procedura: Aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di rimuovere dati da un'origine dati usando le opzioni nell'Interfaccia utente (interfaccia utente) di un elenco o di una web part.|
|[Procedura: Aggiungere un metodo updater](../sharepoint/how-to-add-an-updater-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di modificare i record di dati in un'origine dati direttamente da un elenco o da una web part.|
|[Procedura: Aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Illustra come usare la finestra Dettagli metodo in Visual Studio aggiungere parametri di input e restituiti a un metodo.|
|[Procedura: Definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Viene illustrato come definire i tipi di dati dei parametri nel modello.|
|[Procedura: Definire un'istanza del metodo](../sharepoint/how-to-define-a-method-instance.md)|Viene illustrato come creare un'istanza di un metodo eseguito dal BDC.|
|[Procedura: Aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Illustra come consentire agli utenti di limitare il numero di istanze restituite da un metodo Finder.|
|[Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)|Viene descritto come definire relazioni tra entità nel modello. Le relazioni Web part dati aziendali, gli elenchi esterni e le applicazioni personalizzate possono visualizzare queste relazioni di dati in un'interfaccia utente.|
|[Procedura: Creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)|Illustra come definire le relazioni tra entità nel modello.|
|[Procedura dettagliata: Creare un elenco esterno in SharePoint usando i dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fornisce istruzioni dettagliate che illustrano come creare e testare un modello che visualizza i contatti in un SharePoint esterno.|
|[Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Viene fornita una panoramica della creazione e della progettazione di modelli per il servizio BDC.|
