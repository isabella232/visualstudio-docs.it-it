---
title: Risoluzione dei SharePoint soluzioni | Microsoft Docs
description: Visualizzare i problemi o gli avvisi che possono verificarsi quando si esegue il debug SharePoint soluzioni usando il debugger Visual Studio remoto.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f4c69d5464d23fdeacbb77fb5af7b178a70d2fa5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156234"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Risolvere i SharePoint soluzioni
  Quando si esegue il debug di soluzioni SharePoint tramite il debugger, possono verificarsi i problemi o gli avvisi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] seguenti. Per altre informazioni, vedere [Debugging SharePoint 2007 Workflow Solutions](/previous-versions/bb386166(v=vs.100)).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrizioni dei token nelle web part visive in modalità sandbox
 Tramite le web part visive nelle soluzioni create mediante sandbox non è possibile elaborare i token standard, ad esempio $SPUrl, supportati dal runtime di SharePoint. Di conseguenza, l'URL non viene risolto e non è possibile visualizzare in anteprima il contenuto nella visualizzazione Progettazione nella finestra di progettazione di web part visive se vi si fa riferimento direttamente in un elemento dello script, come nell'esempio seguente:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Per risolvere questa limitazione e il token, farvi riferimento tramite valori letterali:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrizioni dei caratteri nei nomi dei progetti e degli elementi di progetto
 Nei nomi di progetti e di elementi di progetto possono essere inclusi solo caratteri che sono validi in un percorso di distribuzione in SharePoint 2010. Non sono consentiti altri caratteri.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "Caratteri non validi".

### <a name="resolution"></a>Risoluzione
 Per i nomi di progetti e di elementi di progetto di SharePoint, utilizzare solo i caratteri seguenti:

- Caratteri ASCII alfanumerici

- Space

- Punto (.)

- Virgola (,)

- Carattere di sottolineatura (_)

- Trattino (-)

- Barra rovesciata (\\)

  Quando viene creato un pacchetto di un progetto, tramite una regola di convalida viene verificato che nella proprietà del percorso di distribuzione per ogni file distribuito siano contenuti solo questi caratteri validi.

## <a name="errors-when-creating-custom-fields"></a>Errori durante la creazione di campi personalizzati
 I campi personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono definiti in XML. Si possono verificare errori se un campo non è definito o non vi viene fatto riferimento tramite un formato specifico.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "Caratteri non validi" in fase di creazione del pacchetto.

### <a name="resolution"></a>Risoluzione
 L'ID per una definizione di campo deve essere un GUID racchiuso tra parentesi graffe, come illustrato nell'esempio seguente:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Come illustrato nell'esempio seguente, è necessario definire un riferimento a un campo in un tipo di contenuto usando il formato di elemento vuoto ( ), non usando elementi di \<FieldRef /> inizio/fine ( \<FieldRef> \</FieldRef> ):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Se il codice XML di origine per il campo non è corretto, ad esempio un file XML non è valido o presenta altri problemi, si verificherà l'errore indicante che non è possibile analizzare il file.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Le nuove definizioni di sito non in lingua inglese non vengono visualizzate nella pagina di creazione del sito dopo la distribuzione
 Dopo aver creato e distribuito una definizione del sito usando una versione non inglese di (ovvero una versione con impostazioni locali diverse dalla [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 1033),   la scheda Personalizzazioni SharePoint non viene visualizzata nella casella Selezione modello e il nuovo modello di sito non viene visualizzato nella pagina Nuovo **sito SharePoint.**

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica a causa di un valore non corretto nella proprietà **Path** per il file di configurazione della definizione del sito webtemp, ad esempio *webtemp_SiteDefinitionProject1.xml*. Nella proprietà **Path** per il file webtemp, che si trova in **Percorso di** distribuzione, modificare 1033 con le impostazioni locali [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] appropriate. Ad esempio, per usare le impostazioni locali giapponesi, modificare il valore in 1041. Per altre informazioni, vedere [ID delle impostazioni locali assegnati da Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>L'errore viene visualizzato quando un progetto del flusso di lavoro viene distribuito in un sistema pulito
 Questo problema si verifica se si distribuisce un progetto flusso di lavoro in un computer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con un sistema pulito. Un sistema pulito è un computer in cui è presente una nuova installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di SharePoint, ma non sono presenti progetti flusso di lavoro distribuiti.

### <a name="error-message"></a>Messaggio di errore
 Impossibile trovare l'elenco SharePoint: Cronologia flusso di lavoro.

### <a name="resolution"></a>Risoluzione
 Questo errore si verifica a causa di un elenco cronologia del flusso di lavoro mancante. Poiché l'ambiente di sviluppo è un sistema pulito, non vengono distribuiti flussi di lavoro e l'elenco Cronologia flusso di lavoro non esiste ancora. Per risolvere questo problema, riaprire la procedura guidata del flusso di lavoro, che determina la creazione dell'elenco Cronologia flusso di lavoro.

##### <a name="to-reenter-the-workflow-wizard"></a>Per eseguire di nuovo la procedura guidata del flusso di lavoro

1. In **Esplora soluzioni** scegliere il nodo del flusso di lavoro.

2. Nella finestra **Proprietà** scegliere il pulsante con i puntini di sospensione (...) in qualsiasi proprietà con un pulsante con puntini di sospensione.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>L'utente deve aggiornare la pagina dell'applicazione nel browser durante il debug per visualizzare l'immagine aggiornata
 Se si esegue il debug di una soluzione SharePoint che contiene una pagina dell'applicazione con un controllo che visualizza un'immagine, ad esempio un controllo Immagine, è necessario aggiornare la pagina nel browser per visualizzare le modifiche apportate [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] all'immagine.

## <a name="error-the-site-location-is-not-valid"></a>Errore: Il percorso del sito non è valido
 Questo problema può verificarsi se [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] non è installato. Può verificarsi anche se non si ha accesso come amministratore al sito Web SharePoint specificato nella **Personalizzazione** guidata SharePoint .

### <a name="error-message"></a>Messaggio di errore

- SharePoint percorso del sito non è valido.

### <a name="resolution"></a>Risoluzione

- Installare [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Assicurarsi di avere accesso come amministratore al SharePoint Web. Per altre informazioni, vedere [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] l'articolo online [Assegnare o rimuovere amministratori di](/sharepoint/administration/assign-or-remove-administrators-of-service-applications)applicazioni di servizio in SharePoint Server .

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>L'evento Web di eliminazione del sito non si verifica nel progetto del ricevitore di eventi
 Quando si crea un progetto ricevitore di eventi e si selezionano determinati eventi Web, ad esempio "un sito in fase di eliminazione", l'evento non si verifica mai.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica perché l'ambito della funzionalità deve essere "Sito" per gestire gli eventi a livello di sito, ma l'ambito di funzionalità predefinito per i progetti ricevitore di eventi è "Web". Gli eventi Web interessati sono:

- È in corso l'eliminazione di un sito (WebDeleting)

- Un sito è stato eliminato (WebDeleted)

- È in corso lo spostamento di un sito (WebMoving)

- Un sito è stato spostato (WebMoved)

  Per risolvere il problema, modificare l'ambito della funzionalità del ricevitore di eventi, come indicato di seguito.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Per modificare l'ambito della funzionalità del ricevitore di eventi

1. In **Esplora soluzioni** aprire il file con estensione *feature* del ricevitore di eventi in **Progettazione** funzionalità facendo doppio clic sul file o aprendo il relativo menu di scelta rapida e quindi scegliendo **Apri**.

2. Fare clic sulla freccia accanto a **Ambito** e quindi scegliere **Sito** nell'elenco visualizzato.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>L'errore di distribuzione viene visualizzato dopo la modifica del nome di un identificatore in un progetto di modello di connettività dati business
 Questo problema si verifica se si modifica il nome dell'identificatore di un'entità in un modello BDC (Business Data Connectivity) e quindi si prova a distribuire la soluzione.

### <a name="error-messages"></a>messaggi di errore

- \<*model name*> presenta gli errori di attivazione del tipo di contenuto esterno seguenti...

- L'oggetto IMetadataObject con nome \<*model name*> ' ' ha un valore nel campo 'name' duplicato...

### <a name="resolution"></a>Risoluzione
 Per risolvere questo problema, eliminare manualmente il modello e quindi distribuire di nuovo la soluzione.  È possibile eliminare il modello usando uno degli strumenti seguenti:

- SharePoint 2010 Central Administration. Per altre informazioni, vedere [BDC Gestione modelli](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) sul sito Web Microsoft TechNet.

- Windows PowerShell. È possibile eliminare il modello digitando questo comando al prompt dei comandi: **Remove-SPBusinessDataCatalogModel**. Per altre informazioni, vedere [Cmdlet generali (SharePoint Server 2010)](/powershell/module/sharepoint-server) nel sito Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Viene visualizzato un errore quando si tenta di visualizzare una web part visiva in SharePoint
 Questo problema si verifica quando **la proprietà Path** del controllo utente non inizia con la stringa "CONTROLTEMPLATES". \\

### <a name="error-messages"></a>messaggi di errore

- Il file '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* .ascx' non esiste.

- Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione

##### <a name="to-resolve-this-issue"></a>Per risolvere il problema

1. In **Esplora soluzioni** scegliere il file di controllo utente la cui estensione è *ascx.*

2. Sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

3. Nella finestra **Proprietà** espandere il **nodo Percorso di** distribuzione.

4. Assicurarsi che il valore della **proprietà Path** inizi con la stringa "CONTROLTEMPLATES". \\

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>L'errore viene visualizzato quando viene eseguito un flusso di lavoro riutilizzabile importato che contiene un campo modulo attività
 Questo problema si verifica se si importa un flusso di lavoro che contiene un modulo attività con un campo e quindi si esegue il nuovo flusso di lavoro nello stesso sistema da cui è stato importato.

### <a name="error-message"></a>Messaggio di errore
 Si è verificato un errore nel passaggio di distribuzione 'Attiva funzionalità': il campo con ID [*GUID*] definito nella funzionalità [*GUID*] è stato trovato nella raccolta siti corrente o in un sito secondario.

### <a name="resolution"></a>Risoluzione
 Questo errore è il risultato di conflitti di ID campo che si verificano perché il progetto Importa flusso di lavoro riutilizzabile in non modifica gli ID dei campi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del modulo attività. Se si distribuisce un flusso di lavoro importato nello stesso server che contiene il flusso di lavoro originale, si verificano conflitti di ID campo.

 Per risolvere questo problema, usare la funzionalità Trova e sostituisci per modificare il valore dell'attributo ID campo in tutti i file del flusso di lavoro importati.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>L'errore viene visualizzato quando viene eseguita un'istanza dell'elenco importato rinominata
 Questo problema si verifica se si rinomina un'istanza di elenco importata e quindi la si esegue in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

### <a name="error-message"></a>Messaggio di errore
 Errore di compilazione: Si è verificato un errore nel passaggio di distribuzione 'Attiva funzionalità': il file Template\Features \\ [*import project*<em>feature</em>*name*]\Files\Lists [ \\ *old*<em>list name</em>]\Schema.xml does not exist.

### <a name="resolution"></a>Risoluzione
 Quando si importa un'istanza di elenco, viene aggiunto un attributo denominato CustomSchema al file Elements.xml dell'istanza di elenco. Elements.xml include il percorso di un schema.xml personalizzato per l'istanza di elenco. Quando si rinomina l'istanza di elenco in , il percorso di distribuzione per il schema.xml personalizzato cambia, ma il valore del percorso [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dell'attributo CustomSchema non viene aggiornato. Di conseguenza, l'istanza dell'elenco non riesce *a* trovare il fileschema.xmlnel percorso precedente specificato dall'attributo CustomSchema quando la funzionalità viene attivata.

 Per risolvere questo problema, aggiornare il percorso di distribuzione del file *schema.xml* nell'attributo CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint sessione di debug terminata da IIS
 Questo problema si verifica se si imposta un punto di interruzione in una soluzione SharePoint, si sceglie F5 per eseguirlo e quindi si rimane a un punto di interruzione più lungo di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 90  secondi.

### <a name="error-message"></a>Messaggio di errore
 Il processo del server Web di cui è in corso il debug è stato terminato da Internet Information Services (IIS). Il problema può essere risolto configurando le impostazioni ping del pool di applicazioni in IIS. Per altri dettagli, vedere la Guida.

### <a name="resolution"></a>Risoluzione
 Per impostazione predefinita, il pool di applicazioni IIS attende 90 secondi che un'applicazione risponda prima di chiudere l'applicazione. Questo processo è noto come "ping" dell'applicazione. Per risolvere questo problema, è possibile aumentare il tempo di attesa o disabilitare completamente il ping dell'applicazione.

##### <a name="to-access-the-iis-app-pool-settings"></a>Per accedere alle impostazioni del pool di app IIS

1. Aprire Gestione IIS.

2. Nel riquadro **Connessioni** espandere il nodo SharePoint server e quindi scegliere il **nodo Pool di** applicazioni.

3. Nella pagina **Pool di** applicazioni scegliere il pool di applicazioni SharePoint ,in genere "SharePoint -  80", quindi nel riquadro Azioni scegliere il collegamento Impostazioni **avanzate.**

4. Per aumentare il tempo di attesa prima del timeout iis, modificare il valore di **Ping Maximum Response Time (seconds)** su un valore maggiore di 90 secondi.

5. Per disabilitare il ping di IIS, impostare **Ping abilitato** su **False.**

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>La ritirata automatica lascia l'istanza dell'elenco orfana SharePoint
 Questo problema si verifica se si segue questa procedura.

1. Creare una definizione di elenco con un'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Scegliere **il tasto F5** per eseguire la soluzione.

3. Arrestare il debug o chiudere il SharePoint sito.

4. Riaprire SharePoint sito e aprire l'istanza dell'elenco.

### <a name="error-message"></a>Messaggio di errore
 Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione
 Ciò si verifica perché dopo la chiusura di una sessione di debug di una soluzione SharePoint, la funzionalità di ritiro automatico ritrae la soluzione. La ritrazione elimina la definizione dell'elenco SharePoint ma non elimina l'istanza dell'elenco. La definizione dell'elenco sottostante è richiesta dall'istanza di elenco.

 Per risolvere questo problema, distribuire la soluzione scegliendo Compila distribuisci dalla barra dei  >  menu. Non eseguire il debug della soluzione scegliendo **il tasto F5.** Eliminare quindi l'istanza di elenco in SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>La SharePoint originale viene sostituita da una versione esportata
 Se si esporta una soluzione SharePoint, importare la soluzione in e quindi ridistribuirla nello stesso sito da cui è stata esportata, la soluzione SharePoint originale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene sostituita. Questo problema non si verifica se si distribuisce la soluzione in un server in cui non è attivata la soluzione originale.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Per evitare di sovrascrivere una soluzione nel sito da cui è stata esportata, modificare i GUID di SolutionID e gli ID funzionalità di tutte le funzionalità importate nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto.

## <a name="error-appears-when-debugging-starts"></a>All'avvio del debug viene visualizzato un errore
 Quando si avvia il debug di una soluzione SharePoint in Visual Studio, viene visualizzato un errore indicante che è impossibile caricare il file di configurazione Web.config in Visual Studio perché la chiave specificata non è presente nel dizionario.

### <a name="error-message"></a>Messaggio di errore
 Impossibile caricare il file Web.config di configurazione. Controllare la presenza di eventuali elementi XML in formato non valido nel file e riprovare. Si è verificato l'errore seguente: La chiave specificata non era presente nel dizionario.

### <a name="resolution"></a>Risoluzione
 Per risolvere questo problema, verificare che il valore della proprietà URL sito del progetto SharePoint in Visual Studio corrisponda all'URL assegnato all'area predefinita per i mapping di accesso alternativo dell'applicazione Web. L'utilizzo di un'altra area, ad esempio Intranet, per l'URL non risolverà l'errore. L'URL del sito del progetto e l'URL nell'area predefinita devono corrispondere. Per accedere ai mapping di accesso alternativo, aprire l'utilità Amministrazione centrale  SharePoint 2010, scegliere il collegamento Gestione applicazioni e quindi in Applicazioni **Web** scegliere il collegamento Configura mapping di accesso **alternativo.** Per altre informazioni, vedere [Creare zone per applicazioni Web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Vedi anche

- [Risolvere i SharePoint creazione di pacchetti e distribuzione](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debug in Visual Studio](../debugger/debugger-feature-tour.md)