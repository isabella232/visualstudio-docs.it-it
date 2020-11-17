---
title: Progettazione di un modello di integrazione applicativa dei dati | Microsoft Docs
description: Progettare un modello di integrazione applicativa dei dati. Aggiungere entità e metodi. Definire i parametri del metodo. Aggiungere descrittori di filtro. Convalida il modello di integrazione applicativa dei dati.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b574c52b9081cc6640c5611e0759b5559e7a4f6d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672652"
---
# <a name="design-a-business-data-connectivity-model"></a>Progettare un modello di integrazione applicativa dei dati
  È possibile sviluppare un modello per il servizio di integrazione applicativa dei dati mediante l'aggiunta di entità e metodi a un file di modello. Un'entità descrive una raccolta di campi di dati. Un'entità, ad esempio, può rappresentare una tabella in un database. Un metodo esegue un'attività, ad esempio l'aggiunta, l'eliminazione o l'aggiornamento dei dati rappresentati dalle entità. Per altre informazioni, vedere [integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Aggiungi entità
 È possibile aggiungere un'entità trascinando o copiando un' **entità** dalla **casella degli strumenti** di Visual Studio nella finestra di progettazione dell'integrazione applicativa dei dati. Per altre informazioni, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definire i campi dell'entità in una classe. Ad esempio, è possibile aggiungere un campo denominato `Address` a una `Customer` classe. È possibile aggiungere una nuova classe al progetto o usare una classe esistente creata usando altri strumenti, ad esempio la Object Relational Designer (O/R Designer). Il nome dell'entità e il nome della classe che rappresenta l'entità non devono corrispondere. La classe viene correlata all'entità quando si definiscono i metodi nel modello.

## <a name="add-methods"></a>Aggiungi metodi
 Il servizio BDC chiama i metodi nel modello quando gli utenti visualizzano, aggiungono, aggiornano o eliminano informazioni in un elenco o in una Web part basata sul modello. È necessario aggiungere un metodo al modello per ogni attività che l'utente può eseguire. Creare metodi selezionando uno dei cinque tipi di metodo di base dalla finestra **Dettagli metodo di integrazione applicativa dei dati** . Nella tabella seguente vengono descritti i cinque metodi di base di un modello di integrazione applicativa dei dati.

|Metodo|Descrizione|
|------------|-----------------|
|Finder|Restituisce una raccolta di istanze di entità. Chiamato quando l'utente apre l'elenco o la Web part. Per altre informazioni, vedere [procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md).|
|Finder specifico|Restituisce un'istanza di entità specifica. Chiamato quando un utente Visualizza i dettagli di un elemento specifico in un elenco. Per altre informazioni, vedere [procedura: aggiungere un metodo di ricerca specifico](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Autore|Aggiunge nuovi dati all'origine dati di un'entità. Chiamato quando gli utenti scelgono il pulsante **nuovo elemento** sulla barra multifunzione di un elenco basato sul modello. Per altre informazioni, vedere [procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Modifica i dati in un elenco. Chiamato quando gli utenti aggiornano le informazioni in un elenco. Per altre informazioni, vedere [procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Rimuove i dati. Chiamato quando gli utenti eliminano un elemento dall'elenco. Per altre informazioni, vedere [procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definire i parametri del metodo
 Quando si crea un metodo, Visual Studio aggiunge i parametri di input e output appropriati per il tipo di metodo. Questi parametri sono solo segnaposto. Nella maggior parte dei casi, è necessario modificare i parametri in modo che possano passare o restituire il tipo di dati corretto. Per impostazione predefinita, ad esempio, un metodo di ricerca restituisce una stringa. Nella maggior parte dei casi, si vuole modificare il parametro return del metodo Finder in modo che restituisca una raccolta di entità. A tale scopo, è possibile modificare il descrittore di tipo del parametro. Un descrittore di tipo è una raccolta di attributi che descrive il tipo di dati di un parametro. Per altre informazioni, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio consente di copiare i descrittori di tipo tra i parametri nel modello. Ad esempio, è possibile definire un descrittore `CustomerTD` di tipo denominato per il parametro return del `GetCustomer` metodo. È possibile copiare il `CustomerTD` descrittore di tipo in **Esplora integrazione applicativa** dei dati e quindi incollare il descrittore di tipo nel parametro di input del `CreateCustomer` metodo. In questo modo si evita di dover definire più volte lo stesso descrittore di tipo.

## <a name="method-instances"></a>Istanze di metodo
 Quando si crea un metodo, Visual Studio aggiunge un'istanza del metodo predefinito. Un'istanza del metodo è un riferimento a un metodo, oltre ai valori predefiniti per i parametri. Un singolo metodo può avere più istanze di metodo. Ogni istanza è una combinazione della firma del metodo e di un set di valori predefiniti. Per altre informazioni, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Quando si esegue il progetto, le istanze del metodo vengono visualizzate in un elenco a discesa sopra l'elenco di SharePoint. Gli utenti possono scegliere istanze del metodo per visualizzare i dati.

 Per aggiungere valori predefiniti all'istanza del metodo, è necessario modificare direttamente il codice XML del modello. Per ulteriori informazioni, vedere [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Aggiungi descrittori di filtro
 I consumer del modello potrebbero voler recuperare le istanze di un'entità che corrispondono a determinati criteri. Per abilitare questa funzionalità, è possibile aggiungere un descrittore di filtro a un metodo. I descrittori di filtro consentono agli utenti del modello di filtrare i set di risultati del metodo passando i valori ai metodi prima dell'esecuzione. Per altre informazioni, vedere [procedura: aggiungere parametri di filtro alle operazioni per limitare le istanze dal sistema esterno](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 In SharePoint sono disponibili diverse funzionalità che consentono agli utenti di fornire i valori di filtro. Ad esempio, i dati di Business Web part forniscono una casella di testo del filtro. Gli utenti possono limitare i dati in un elenco immettendo un valore nella casella di testo. Per altre informazioni su come aggiungere un descrittore di filtro a un metodo, vedere [procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Proprietà del descrittore di filtro
 È necessario impostare il valore del **descrittore di tipo associato**, il **nome** e le proprietà del **tipo** di un descrittore di filtro. Tutte le altre proprietà sono facoltative.

 La proprietà del **descrittore di tipo associato** correla il descrittore di filtro a un parametro di input. Quando un utente fornisce un valore di filtro, il servizio BDC passa tale valore al metodo utilizzando il parametro di input.

 La proprietà **Type** descrive il modello di filtro che si desidera utilizzare. In SharePoint, il criterio di filtro selezionato influiscono sul testo visualizzato nell'interfaccia utente (UI). Per un criterio di filtro di confronto, ad esempio, il testo **è uguale a** viene visualizzato come controllo sopra una Web part dati business. Per ulteriori informazioni su ogni modello di filtro, vedere [tipi di filtri supportati da integrazione applicativa](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))dei dati.

 Per ulteriori informazioni sulle proprietà di un descrittore di filtro, vedere [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Specificare i valori predefiniti
 In alcuni casi, è possibile che l'utente non fornisca un valore di filtro. È possibile specificare un valore predefinito aggiungendo un valore predefinito all'istanza del metodo oppure impostando il valore predefinito nel codice del metodo. Per ulteriori informazioni sull'aggiunta di un valore predefinito all'istanza del metodo, vedere [oggetto MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Per un esempio di come impostare il valore predefinito di un parametro di input nel codice del metodo, vedere [procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Convalidare il modello
 È possibile convalidare il modello durante lo sviluppo. Visual Studio identifica i problemi che possono impedire il comportamento del modello come previsto. Questi problemi vengono visualizzati nel **Elenco errori** di Visual Studio.

 È possibile convalidare un modello aprendo il menu di scelta rapida per la finestra di progettazione BDC e scegliendo **convalida**. Se il modello contiene errori, questi vengono visualizzati nel **Elenco errori**. È possibile spostare rapidamente il cursore sul codice contenente un errore facendo doppio clic sull'errore nell'elenco. In alternativa, è possibile scegliere i tasti **F8** o **MAIUSC** + **F8** ripetutamente per spostarsi avanti o indietro negli errori dell'elenco.

 Gli errori di convalida possono verificarsi quando le regole del modello vengono violate in qualche modo. Se, ad esempio, la proprietà **myCollection** di un descrittore di tipo è impostata su **true**, ma non esistono descrittori di tipo figlio, verrà visualizzato un errore di convalida. Potrebbe essere necessario fare riferimento alle regole di un modello di integrazione applicativa dei dati per comprendere alcuni errori visualizzati nel **Elenco errori** di Visual Studio. Per ulteriori informazioni sulle regole di un modello di integrazione applicativa dei dati, vedere [Schema BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Eseguire il debug della soluzione che contiene il modello
 È possibile eseguire il debug del codice durante il debug di qualsiasi codice in Visual Studio. Per eseguire il debug del codice, impostare i punti di interruzione in qualsiasi punto del codice e quindi avviare il debugger. Visual Studio apre il sito di SharePoint. In SharePoint creare un elenco o una Web part che utilizza i dati aziendali. Quindi, è possibile eseguire il codice un'istruzione alla volta. Per ulteriori informazioni sul debug di progetti SharePoint, vedere [risolvere i problemi relativi alle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 È anche possibile eseguire il debug del codice negli assembly personalizzati che si aggiungono al progetto. Tuttavia, per eseguire il debug del codice in un assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione. Per altre informazioni, vedere [procedura: aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Per ulteriori informazioni sull'aggiunta di un assembly personalizzato al progetto, vedere [procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)dei dati.

### <a name="configure-bdc-security"></a>Configurare la sicurezza BDC
 Per poter eseguire il debug della soluzione, potrebbe essere necessario modificare le impostazioni di sicurezza in SharePoint. Per modificare queste impostazioni, aprire l'applicazione del servizio di integrazione applicativa dei dati nel sito Web di amministrazione centrale SharePoint 2010. Nella finestra di dialogo **Imposta autorizzazioni archivio metadati** aggiungere l'account utente e quindi selezionare una delle opzioni seguenti:

|Attività|Opzione|
|----------|------------|
|Per distribuire modelli al servizio integrazione applicativa dei dati.|Modifica|
|Per creare elenchi e Web part utilizzando i tipi di contenuto esterni (entità) nel modello.|Selezionabile nei client|
|Per creare, leggere, aggiornare ed eliminare dati di entità.|Execute|

 Per ulteriori informazioni su queste impostazioni, vedere [Business Data Connectivity Service Management](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 È anche possibile impostare le autorizzazioni di sicurezza per i singoli modelli o i tipi di contenuto esterno. Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un modello, vedere [gestione dei modelli di integrazione applicativa](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14))dei dati. Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un tipo di contenuto esterno, vedere [gestione dei tipi di contenuto esterno](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Usare queste impostazioni per eseguire il debug di una soluzione nel server SharePoint locale. Per ulteriori informazioni su come configurare le impostazioni di sicurezza relative a BDC nel server SharePoint di produzione, vedere [Panoramica della sicurezza di servizi di integrazione applicativa dei dati](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Ritirare i modelli che risultano danneggiati
 Quando il debugger viene avviato per la prima volta, in Visual Studio l'intero modello viene distribuito in SharePoint. Per ogni volta successivamente, Visual Studio aggiorna il modello in SharePoint con le eventuali modifiche apportate tra le distribuzioni.

 Potrebbero essere presenti situazioni in cui si desidera che Visual Studio ritragga completamente il modello da SharePoint. Ad esempio, un modello potrebbe essere danneggiato.  Per ridistribuire il modello in SharePoint, impostare la proprietà **aggiornamento incrementale** del modello su **false**, quindi avviare il debugger. La proprietà **aggiornamento incrementale** viene visualizzata nella finestra **Proprietà** di quando si seleziona il nodo che rappresenta il modello in **Esplora integrazione applicativa** dei dati. Per impostazione predefinita, il nome del modello è **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modificare i nomi degli identificatori delle entità nel modello
 Se si modifica il nome di un identificatore dopo la distribuzione del modello, è possibile che venga visualizzato un errore di distribuzione. Non è possibile risolvere questo errore impostando la proprietà **aggiornamento incrementale** del modello su **false**. È necessario ritirare il modello manualmente, quindi distribuire nuovamente la soluzione. Per ulteriori informazioni, vedere [risolvere i problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). È possibile evitare questo errore impostando la proprietà **aggiornamento incrementale** su **false** prima di distribuire inizialmente il modello.

## <a name="locate-documentation-for-bdc-model-elements"></a>Individuare la documentazione per gli elementi del modello BDC
 Visual Studio aggiunge un elemento XML al modello per ogni entità, metodo o altro elemento creato. Gli attributi degli elementi vengono visualizzati come proprietà nella finestra **Proprietà** . Per informazioni sugli elementi e sugli attributi generati da Visual Studio durante la progettazione del modello, vedere [Schema BDCMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)|Vengono descritti gli strumenti che è possibile utilizzare per progettare visivamente un modello per l'integrazione applicativa dei dati.|
|[Procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md)|Viene illustrato come aggiungere al modello tipi di contenuto esterni, o entità.|
|[Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di visualizzare un elenco di entità in un elenco o in una Web part.|
|[Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di visualizzare i dettagli di un'entità specifica.|
|[Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di aggiungere record a un'origine dati direttamente da un elenco o una Web part.|
|[Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di rimuovere dati da un'origine dati utilizzando le opzioni nell'interfaccia utente di un elenco o di una Web part.|
|[Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di modificare i record di dati in un'origine dati direttamente da un elenco o una Web part.|
|[Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Viene illustrato come utilizzare la finestra Dettagli metodo in Visual Studio per aggiungere parametri di input e restituiti a un metodo.|
|[Procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Viene illustrato come definire i tipi di dati dei parametri nel modello.|
|[Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)|Viene illustrato come creare un'istanza di un metodo eseguito dall'integrazione applicativa dei dati.|
|[Procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Viene illustrato come consentire agli utenti di limitare il numero di istanze restituite da un metodo Finder.|
|[Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)|Viene descritto come è possibile definire le relazioni tra entità nel modello. I dati aziendali Web part, gli elenchi esterni e le applicazioni personalizzate possono visualizzare queste relazioni tra i dati in un'interfaccia utente (UI).|
|[Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)|Viene illustrato come definire le relazioni tra entità nel modello.|
|[Procedura dettagliata: creareun elenco esterno in SharePoint tramite dati aziendali](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Vengono fornite istruzioni dettagliate in cui viene illustrato come creare e testare un modello che Visualizza i contatti in un elenco esterno di SharePoint.|
|[Integrare i dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Viene fornita una panoramica della creazione e della progettazione di modelli per il servizio di integrazione applicativa dei dati.|
