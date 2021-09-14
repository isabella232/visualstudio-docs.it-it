---
title: Importazione di elementi da un sito SharePoint esistente | Microsoft Docs
description: Importare elementi da un sito SharePoint esistente con il modello di progetto Importa pacchetto soluzione SharePoint, in modo da poter riutilizzare gli elementi in una nuova SharePoint soluzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 752e65412cc7ee7b3179f47ecd27caaf4e088822
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711407"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importare elementi da un sito SharePoint esistente
  Il modello di progetto Importa pacchetto di soluzione SharePoint consente di riutilizzare elementi come i campi e i tipi di contenuto da siti di SharePoint esistenti in una nuova soluzione SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sebbene sia possibile eseguire la maggior parte delle soluzioni importate senza modifiche, esistono alcune limitazioni e problemi da tenere in considerazione, soprattutto se si modificano gli elementi dopo averli importati.

> [!NOTE]
> Per importare flussi di lavoro riutilizzabili, usare il modello di progetto Importa flusso di lavoro riutilizzabile. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Linee guida per l'importazione di flussi di lavoro riutilizzabili.](../sharepoint/guidelines-for-importing-reusable-workflows.md)

## <a name="supported-sharepoint-solutions"></a>Soluzioni SharePoint supportate
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] supporta pienamente l'importazione delle soluzioni create in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] non supporta l'importazione di soluzioni create nelle applicazioni seguenti:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Anche se spesso è possibile importare correttamente soluzioni create da queste applicazioni, la funzionalità non è stata testata e non è supportata.

## <a name="item-import-restrictions"></a>Restrizioni per l'importazione di elementi
 Sebbene la maggior SharePoint elementi possa essere importata da un file con estensione *wsp* esistente, gli elementi seguenti non sono supportati e possono richiedere modifiche per il corretto funzionamento:

- Entità BDC

- Elementi di associazione del flusso di lavoro di codice.

- Flussi di lavoro di codice

- Web part visive (.ascx)

- Servizi Web (*.asmx*)

- Associazioni al tipo di contenuto

- Ricevitori di eventi

- Definizioni di elenco (modelli)

- Definizioni di sito

  Quando si esporta una soluzione da [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o , questi elementi vengono [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] automaticamente esclusi dal file con estensione *wsp.* Tuttavia, altri *file con estensione wsp* generati da strumenti non supportati possono contenere questi elementi. Vedere "Soluzioni SharePoint supportate" più indietro in questo articolo.

## <a name="what-happens-when-you-import-a-solution"></a>Cosa accade quando si importa una soluzione
 Quando si importa una soluzione con il modello Importa pacchetto soluzione SharePoint, copia tutto il contenuto del file con estensione wsp e tenta di riconciliare e mantenere il maggior numero possibile di associazioni e riferimenti tra gli elementi importati e i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] relativi file. 

 Tutti gli elementi importati vengono copiati nelle cartelle corrispondenti in **Esplora soluzioni**. Ad esempio, i tipi di contenuto vengono visualizzati nella cartella **Tipi di contenuto** e le istanze di elenco vengono visualizzate in **Istanze elenco**. I file associati a un elemento importato vengono copiati anche nella cartella dell'elemento. Ad esempio, un'istanza di elenco importata include i moduli, i form e le pagine ASPX corrispondenti.

### <a name="dependent-items"></a>Elementi dipendenti
 Se si seleziona un elemento nella procedura guidata Importa pacchetto di soluzione SharePoint, ma non i relativi elementi dipendenti, una finestra di messaggio indica che è necessario selezionare anche gli elementi dipendenti prima dell'importazione.

### <a name="what-are-features"></a>Che cosa sono le funzionalità?
 Gli utenti di SharePoint Designer potrebbero vedere file imprevisti, denominati *caratteristiche*, nelle soluzioni importate in **Esplora soluzioni.** Sebbene esistessero, erano nascoste nella soluzione di SharePoint Designer. Ora sono visibili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Le funzionalità sono contenitori per gli elementi di SharePoint. Ogni caratteristica mantiene un riferimento a ogni elemento che contiene, ad esempio tipi di contenuto e definizioni di elenco. Quando si importa la soluzione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] configura le caratteristiche per tutti gli elementi importati e tenta di mantenere le relazioni funzionalità-elemento per i file. Tutti i file per cui non è possibile risolvere i riferimenti vengono inseriti nella cartella **Altri file importati** .

 Per altre informazioni sulle funzionalità, vedere [Sviluppare SharePoint soluzioni](../sharepoint/developing-sharepoint-solutions.md) e Uso delle [funzionalità](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Gestire casi speciali
 In alcuni casi, Visual Studio non è in grado di riconciliare un elemento con i file dipendenti. Tutti i file che [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non è in grado di risolvere vengono inseriti nella cartella **Altri file importati**. Inoltre, le relative proprietà **DeploymentType** vengono impostate su **NoDeployment** per evitarne la distribuzione con la soluzione.

 Ad esempio, se si importa la definizione di elenco ExpenseForms, una definizione di elenco  con tale nome viene visualizzata nella cartella **Definizioni** elenco in **Esplora soluzioni** insieme ai relativiElements.xmle *Schema.xml* file. Tuttavia, i form ASPX e HTML associati possono essere inseriti in una cartella denominata **ExpenseForms** nella cartella **Altri file importati** . Per completare l'importazione, spostare i file nella definizione di elenco ExpenseForms in **Esplora soluzioni** e modificare la proprietà **DeploymentType** per ogni file da **NoDeployment** a **ElementFile**.

 Quando si importano ricevitori di eventi, il *file* Elements.xmlviene copiato nel percorso corretto, ma è necessario includere manualmente l'assembly nel pacchetto della soluzione in modo che sia distribuito con la soluzione. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)]Per informazioni su come eseguire questa operazione, [vedere Procedura: Aggiungere e rimuovere assembly aggiuntivi.](../sharepoint/how-to-add-and-remove-additional-assemblies.md)

 Quando si importano i flussi di lavoro, i moduli di InfoPath vengono copiati nella cartella **Altri file importati** . Se il file *con estensione wsp* contiene un modello Web, viene impostato come pagina di avvio in **Esplora soluzioni**.

## <a name="import-fields-and-property-bags"></a>Importare campi e sacchetti di proprietà
 Quando si importa una soluzione con **più** campi, tutte le definizioni di campo separate vengono unite in un singolo file *Elements.xml* in un nodo in Esplora soluzioni **denominato Campi**. Analogamente, tutte le voci del contenitore di proprietà vengono unite in un file *Elements.xml* in un nodo denominato **PropertyBags**.

 I campi in SharePoint sono colonne di un determinato tipo di dati, ad esempio testo, booleano o ricerca. Per altre informazioni, vedere [Blocco predefinito: Colonne e tipi di campo](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). I contenitori delle proprietà consentono di aggiungere proprietà in vari oggetti in SharePoint, da una farm a un elenco in un sito di SharePoint. I contenitori delle proprietà vengono implementati come tabella hash di nomi di proprietà e valori. Per altre informazioni, vedere la pagina relativa alla [gestione della configurazione di SharePoint](/previous-versions/msp-n-p/ff647766(v=pandp.10)) oppure quella relativa alle [impostazioni del contenitore delle proprietà di SharePoint](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Eliminare elementi nel progetto
 La maggior parte degli elementi nelle soluzioni di SharePoint ha uno o più elementi dipendenti. Ad esempio, le istanze di elenco dipendono dai tipi di contenuto e i tipi di contenuto dipendono dai campi. Dopo avere importato una soluzione di SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non notifica i problemi relativi ai riferimenti se si elimina un elemento nella soluzione ma non i relativi elementi dipendenti, fino a quando non si tenta di distribuire la soluzione. Ad esempio, se una soluzione importata include un'istanza di elenco che dipende da un tipo di contenuto che viene eliminato, è possibile che si verifichi un errore al momento della distribuzione. L'errore si verifica quando l'elemento dipendente non è presente nel server SharePoint. Analogamente, se un elemento eliminato ha anche un contenitore di proprietà correlato, eliminare le voci del contenitore di proprietà dal *file* **Elements.xmlPropertyBags.** Di conseguenza, se si eliminano tutti gli elementi da una soluzione importata e vengono generati errori di distribuzione, verificare se devono essere eliminati anche tutti gli elementi dipendenti.

## <a name="restore-missing-feature-attributes"></a>Ripristinare gli attributi delle funzionalità mancanti
 Quando si importano soluzioni, alcuni attributi di funzionalità facoltativi vengono omessi dal manifesto della funzionalità importate. Se si desidera ripristinare questi attributi nel nuovo file di funzionalità, identificare gli attributi mancanti confrontando il file di funzionalità originale con il nuovo manifesto della funzionalità e seguire le istruzioni nell'argomento [Procedura:](../sharepoint/how-to-customize-a-sharepoint-feature.md)Personalizzare una funzionalità SharePoint .

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Il rilevamento dei conflitti di distribuzione non viene eseguito nelle istanze di elenco predefinite
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] non esegue il rilevamento dei conflitti di distribuzione sulle istanze di elenco incorporate, ovvero le istanze di elenco predefinite fornite con SharePoint. Il rilevamento dei conflitti non viene eseguito per evitare di sovrascrivere le istanze di elenco incorporate su SharePoint. Le istanze di elenco incorporate vengono ancora distribuite o aggiornate, ma non vengono mai eliminate o sovrascritte. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Risolvere i SharePoint la creazione di pacchetti e la distribuzione.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="import-sharepoint-server-2010-workflows"></a>Importare SharePoint flussi di lavoro di Server 2010
 Se si importa un flusso di lavoro creato in [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], non verrà eseguito correttamente dopo averlo distribuito. Tale flusso di lavoro non viene eseguito correttamente a causa della mancanza di alcuni assembly e della presenza nei flussi di lavoro di  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] di form InfoPath non attualmente supportati nelle soluzioni flusso di lavoro di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . È comunque possibile ottenere un funzionamento corretto dei flussi di lavoro di [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] importati dopo avere corretto alcuni elementi, ad esempio aggiungendo riferimenti agli assembly di [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] e riconnettendo i form InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importazione SharePoint flussi di lavoro di Server 2010](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Limite di caratteri per il nome dell'elemento
 In[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i nomi dei progetti e degli elementi di progetto hanno un limite di 260 caratteri in totale, compreso il percorso Se un nome di elemento supera tale limite quando si importa una soluzione, viene generato l'errore:

 **Il percorso, il nome file o entrambi specificati sono troppo lunghi. Il nome file completo deve essere minore di 260 caratteri e il nome della directory deve essere minore di 248 caratteri.**

 Quando viene visualizzato questo errore, l'elemento non viene creato. Questo problema si verifica più spesso nei moduli importati. Per evitare questo problema, eseguire le operazioni seguenti:

- Quando si immettono nomi di progetti nella finestra di dialogo **Aggiungi nuovo progetto** , usare nomi brevi.

- Creare il progetto in una posizione il più vicino possibile alla cartella radice, in modo da abbreviare il percorso.

## <a name="the-sharepointproductversion-attribute"></a>Attributo SharePointProductVersion
 Quando si importa una soluzione creata in una versione precedente di SharePoint come [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], impostare il valore dell'attributo SharePointProductVersion su 12.0 nel manifesto del pacchetto o inserire un controllo di gestione script in tutte le pagine Web importate e lasciare l'attributo SharePointProductVersion impostato su 14.0. In caso contrario, i Web Form importati non vengono visualizzati in SharePoint.

### <a name="background"></a>Sfondo
 Le soluzioni in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] includono un attributo denominato SharePointProductVersion. In SharePoint questo attributo viene usato nei manifesti di pacchetto per determinare la versione di SharePoint per cui è progettata la soluzione. I due valori validi sono 12.0 e 14.0. Il valore 12.0 indica che l'elemento è progettato per [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], mentre il valore 14.0 indica che l'elemento è progettato per [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 Per maggiore sicurezza durante il rendering di pagine ASPX, [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] e [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] richiedono che tutte le pagine master o ASPX contengano un controllo di gestione di script. Per altre informazioni sul gestore di script, vedere [Panoramica del controllo ScriptManager](/previous-versions/bb398863(v=vs.140)). Dato che il controllo di gestione script non è disponibile in [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] e [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], è necessario aggiungerne uno a qualsiasi pagina di [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] che venga aggiornata a [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Le pagine ASPX che usano una pagina master standard non richiedono un controllo di gestione di script perché ne è già stato aggiunto uno alla pagina master standard. Per le pagine ASPX che non usano una pagina master o che usano una pagina master personalizzata, invece, è necessario aggiungere un controllo script per consentirne il funzionamento in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

 L'assenza di un controllo di gestione di script può costituire un problema quando si importa un progetto di [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] in [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]perché l'attributo SharePointProductVersion di tutti i nuovi progetti viene impostato su 14.0. Se si distribuisce un progetto aggiornato che ha un Web Form senza gestore di script, non sarà possibile visualizzare il form in SharePoint.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Importare elementi da un sito SharePoint esistente](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Linee guida per l'importazione di flussi di lavoro riutilizzabili](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Procedura dettagliata: Importare un flusso SharePoint designer riutilizzabile in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
