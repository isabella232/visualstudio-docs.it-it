---
title: Risoluzione dei problemi relativi alle soluzioni SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fcb30056021a865d0b0e605de462ff72ced5a383
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661891"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Risolvere i problemi relativi alle soluzioni SharePoint
  Quando si esegue il debug di soluzioni SharePoint tramite il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], potrebbero verificarsi i problemi o gli avvisi seguenti. Per altre informazioni, vedere [debug di soluzioni flusso di lavoro SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrizioni relative ai token nelle web part visive create mediante sandbox
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

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Limitazioni dei caratteri nei nomi di progetti e di elementi di progetto
 Nei nomi di progetti e di elementi di progetto possono essere inclusi solo caratteri che sono validi in un percorso di distribuzione in SharePoint 2010. Non sono consentiti altri caratteri.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "caratteri non validi".

### <a name="resolution"></a>Risoluzione
 Per i nomi di progetti e di elementi di progetto di SharePoint, utilizzare solo i caratteri seguenti:

- Caratteri ASCII alfanumerici

- Spazio

- Punto (.)

- Virgola (,)

- Carattere di sottolineatura (_)

- Trattino (-)

- Barra rovesciata (\\)

  Quando viene creato un pacchetto di un progetto, tramite una regola di convalida viene verificato che nella proprietà del percorso di distribuzione per ogni file distribuito siano contenuti solo questi caratteri validi.

## <a name="errors-when-creating-custom-fields"></a>Errori durante la creazione di campi personalizzati
 I campi personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono definiti in XML. Si possono verificare errori se un campo non è definito o non vi viene fatto riferimento tramite un formato specifico.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "caratteri non validi" in fase di creazione del pacchetto.

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

 Come illustrato nell'esempio seguente, un riferimento a un campo in un tipo di contenuto deve essere definito usando il formato di elemento vuoto (\<FieldRef/>), non usando gli elementi Start/End (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Se il codice XML di origine per il campo non è corretto, ad esempio un file XML non è valido o presenta altri problemi, si verificherà l'errore indicante che non è possibile analizzare il file.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Le nuove definizioni di sito non in lingua inglese non vengono visualizzate nella pagina di creazione del sito dopo la distribuzione
 Dopo aver creato e distribuito una definizione di sito utilizzando una versione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non in lingua inglese, ovvero una versione con impostazioni locali [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] diverse da 1033, la scheda **personalizzazioni di SharePoint** non viene visualizzata nella casella di **selezione del modello** e nel nuovo sito il modello non viene visualizzato nella pagina **nuovo sito di SharePoint** .

### <a name="error-message"></a>Messaggio di errore
 Nessuna.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica a causa di un valore non corretto nella proprietà **path** per il file di configurazione della definizione sito Webtemp, ad esempio *webtemp_SiteDefinitionProject1. XML*. Nella proprietà **path** per il file WebTemp, situato nel percorso di **distribuzione**, impostare 1033 sulle impostazioni locali appropriate [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ad esempio, per usare le impostazioni locali giapponesi, modificare il valore in 1041. Per ulteriori informazioni, vedere [ID delle impostazioni locali assegnati da Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Errore visualizzato quando un progetto flusso di lavoro viene distribuito in un sistema pulito
 Questo problema si verifica se si distribuisce un progetto flusso di lavoro in un computer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con un sistema pulito. Un sistema pulito è un computer in cui è presente una nuova installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di SharePoint, ma non sono presenti progetti flusso di lavoro distribuiti.

### <a name="error-message"></a>Messaggio di errore
 Impossibile trovare l'elenco di SharePoint: cronologia del flusso di lavoro.

### <a name="resolution"></a>Risoluzione
 Questo errore si verifica a causa di un elenco di cronologia del flusso di lavoro mancante. Poiché l'ambiente di sviluppo è un sistema pulito, non vengono distribuiti flussi di lavoro e l'elenco della cronologia del flusso di lavoro non esiste ancora. Per risolvere questo problema, riaprire la creazione guidata del flusso di lavoro, che determina la creazione dell'elenco cronologia del flusso di lavoro.

##### <a name="to-reenter-the-workflow-wizard"></a>Per immettere nuovamente la creazione guidata flusso di lavoro

1. In **Esplora soluzioni**scegliere il nodo flusso di lavoro.

2. Nella finestra **Proprietà** scegliere il pulsante con i puntini di sospensione (...) in qualsiasi proprietà con un pulsante con i puntini di sospensione.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>L'utente deve aggiornare la pagina dell'applicazione nel browser durante il debug per visualizzare l'immagine aggiornata
 Se si esegue il debug di una soluzione SharePoint che contiene una pagina dell'applicazione con un controllo che visualizza un'immagine, ad esempio un controllo [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] immagine, è necessario aggiornare la pagina nel browser per visualizzare le modifiche apportate all'immagine.

## <a name="error-the-site-location-is-not-valid"></a>Errore: il percorso del sito non è valido
 Questo problema può verificarsi se [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] non è installato. Questo problema può verificarsi anche se non si dispone dell'accesso di amministratore al sito Web di SharePoint specificato nella **procedura guidata di personalizzazione di SharePoint**.

### <a name="error-message"></a>Messaggio di errore

- Il percorso del sito di SharePoint non è valido.

### <a name="resolution"></a>Risoluzione

- Come requisito minimo, installare la console di [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Assicurarsi di disporre dell'accesso amministrativo al sito Web di SharePoint. Per ulteriori informazioni, vedere l'articolo [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] online [assegnare o rimuovere gli amministratori delle applicazioni di servizio in SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>L'evento Web di eliminazione sito non si verifica nel progetto ricevitore di eventi
 Quando si crea un progetto di ricevitore di eventi e si selezionano alcuni eventi Web, ad esempio "è in corso l'eliminazione di un sito", l'evento non si verifica mai.

### <a name="error-message"></a>Messaggio di errore
 Nessuna.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica perché l'ambito di funzionalità deve essere "sito" per gestire gli eventi a livello di sito, ma l'ambito di funzionalità predefinito per i progetti di ricevitore di eventi è "Web". Gli eventi Web interessati sono:

- È in corso l'eliminazione di un sito (webdeletion)

- Un sito è stato eliminato (WebDeleted)

- È in corso lo spostamento di un sito (webmoveing)

- Un sito è stato spostato (WebMoved)

  Per risolvere il problema, modificare l'ambito della funzionalità del ricevitore di eventi, come indicato di seguito.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Per modificare l'ambito della funzionalità del ricevitore di eventi

1. In **Esplora soluzioni**aprire il file con *estensione feature* del ricevitore di eventi in **Progettazione funzionalità** facendo doppio clic sul file o aprendo il menu di scelta rapida e scegliendo **Apri**.

2. Scegliere la freccia accanto a **ambito**, quindi scegliere **sito** nell'elenco visualizzato.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Viene visualizzato un errore di distribuzione dopo la modifica del nome di un identificatore in un progetto di modello di integrazione applicativa dei dati
 Questo problema si verifica se si modifica il nome dell'identificatore di un'entità in un modello di integrazione applicativa dei dati e quindi si tenta di distribuire la soluzione.

### <a name="error-messages"></a>Messaggi di errore

- il *nome del modello*di \<> presenta i seguenti errori di attivazione del tipo di contenuto esterno...

- Il valore di IMetadataObject con nome '\<*nome modello*>' contiene un valore nel campo ' nome ' duplicato...

### <a name="resolution"></a>Risoluzione
 Per risolvere il problema, eliminare il modello manualmente, quindi distribuire nuovamente la soluzione.  È possibile eliminare il modello utilizzando uno degli strumenti seguenti:

- Amministrazione centrale SharePoint 2010. Per ulteriori informazioni, vedere [Gestione modelli BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) sul sito Web Microsoft TechNet.

- Windows PowerShell. È possibile eliminare il modello digitando questo comando al prompt dei comandi: **Remove-SPBusinessDataCatalogModel**. Per ulteriori informazioni, vedere [cmdlet generali (SharePoint Server 2010)](/powershell/module/sharepoint-server) sul sito Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Quando si tenta di visualizzare una Web part visiva in SharePoint, viene visualizzato un errore
 Questo problema si verifica quando la proprietà **path** del controllo utente non inizia con la stringa "controltemplates\\".

### <a name="error-messages"></a>Messaggi di errore

- Il file '/_CONTROLTEMPLATES/ *\<nome del progetto >* / *\<nome della web part >* /\<il *nome del controllo utente >* . ascx ' non esiste.

- Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione

##### <a name="to-resolve-this-issue"></a>Per risolvere il problema

1. In **Esplora soluzioni**scegliere il file di controllo utente, il cui estensione di file è *ascx*.

2. Nella barra dei menu scegliere **visualizza** > **finestra Proprietà**.

3. Nella finestra **Proprietà** espandere il nodo **percorso di distribuzione** .

4. Verificare che il valore della proprietà **path** inizi con la stringa "controltemplates\\".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Viene visualizzato un errore quando viene eseguito un flusso di lavoro riutilizzabile importato contenente un campo del modulo attività
 Questo problema si verifica se si importa un flusso di lavoro che contiene un form attività con un campo, quindi si esegue il nuovo flusso di lavoro nello stesso sistema da cui è stato importato.

### <a name="error-message"></a>Messaggio di errore
 Si è verificato un errore durante il passaggio di distribuzione ' attiva funzionalità': il campo con ID [*GUID*] definito nella funzionalità [*GUID*] è stato trovato nella raccolta siti corrente o in un sito secondario.

### <a name="resolution"></a>Risoluzione
 Questo errore è il risultato di conflitti ID campo che si verificano perché il progetto di flusso di lavoro di importazione riutilizzabile in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non modifica gli ID dei campi del form attività. Se si distribuisce un flusso di lavoro importato nello stesso server che contiene il flusso di lavoro originale, si verificano conflitti di ID campo.

 Per risolvere questo problema, utilizzare la funzionalità Trova e Sostituisci per modificare il valore dell'attributo field ID in tutti i file del flusso di lavoro importati.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Errore visualizzato quando viene eseguita un'istanza di elenco importata rinominata
 Questo problema si verifica se si rinomina un'istanza di elenco importata e quindi la si esegue in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Messaggio di errore
 Errore di compilazione: si è verificato un errore nel passaggio di distribuzione ' attiva funzionalità': il file Template\Features\\[*Importa* *nome*della<em>funzionalità</em>del progetto] \Files\Lists\\[<em>nome elenco</em>*precedente*] \Schema.XML non esiste.

### <a name="resolution"></a>Risoluzione
 Quando si importa un'istanza di elenco, viene aggiunto un attributo denominato CustomSchema al file Elements. XML dell'istanza dell'elenco. Elements. XML include il percorso di uno schema. XML personalizzato per l'istanza dell'elenco. Quando si rinomina l'istanza dell'elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il percorso di distribuzione per lo schema personalizzato XML viene modificato, ma il valore del percorso dell'attributo CustomSchema non viene aggiornato. Di conseguenza, l'istanza di elenco non è in grado di trovare il file *schema. XML* nel percorso precedente specificato dall'attributo CustomSchema quando la funzionalità è attivata.

 Per risolvere questo problema, aggiornare il percorso del percorso di distribuzione del file *schema. XML* nell'attributo CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Sessione di debug di SharePoint terminata da IIS
 Questo problema si verifica se si imposta un punto di interruzione in una soluzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint, si preme il tasto **F5** per eseguirla e quindi si rimane in corrispondenza di un punto di interruzione superiore a 90 secondi.

### <a name="error-message"></a>Messaggio di errore
 Il processo del server Web di cui è in corso il debug è stato terminato da Internet Information Services (IIS). Il problema può essere risolto configurando le impostazioni ping del pool di applicazioni in IIS. Per ulteriori informazioni, vedere la guida.

### <a name="resolution"></a>Risoluzione
 Per impostazione predefinita, il pool di applicazioni IIS attende 90 secondi prima che un'applicazione risponda prima di chiudere l'applicazione. Questo processo è noto come "ping" dell'applicazione. Per risolvere questo problema, è possibile aumentare il tempo di attesa o disabilitare completamente il ping dell'applicazione.

##### <a name="to-access-the-iis-app-pool-settings"></a>Per accedere alle impostazioni del pool di applicazioni IIS

1. Aprire Gestione IIS.

2. Nel riquadro **connessioni** espandere il nodo server SharePoint, quindi scegliere il nodo Pool di **applicazioni** .

3. Nella pagina **pool di applicazioni** selezionare il pool di applicazioni di SharePoint (in genere "SharePoint-80"), quindi fare clic sul collegamento **Impostazioni avanzate** nel riquadro **azioni** .

4. Per aumentare il tempo di attesa prima del timeout di IIS, modificare il valore del **tempo massimo di risposta ping (secondi)** in un valore superiore a 90 secondi.

5. Per disabilitare il ping di IIS, impostare **Ping abilitato** su **false**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Ritrazione automatica lascia l'istanza dell'elenco orfano in SharePoint
 Questo problema si verifica se si esegue la procedura seguente.

1. Creare una definizione di elenco con un'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Premere il tasto **F5** per eseguire la soluzione.

3. Arrestare il debug o chiudere il sito di SharePoint.

4. Riaprire il sito di SharePoint e aprire l'istanza dell'elenco.

### <a name="error-message"></a>Messaggio di errore
 Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica perché dopo la chiusura di una sessione di debug di una soluzione SharePoint, la funzionalità di ritrazione automatica ritrae la soluzione. La ritrazione Elimina la definizione dell'elenco da SharePoint, ma non elimina l'istanza dell'elenco. La definizione dell'elenco sottostante è richiesta dall'istanza dell'elenco.

 Per risolvere questo problema, distribuire la soluzione dalla barra dei menu, scegliendo **compila** > **Distribuisci**. Non eseguire il debug della soluzione scegliendo il tasto **F5** . Eliminare quindi l'istanza dell'elenco in SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>La soluzione SharePoint originale viene sostituita da una versione esportata
 Se si esporta una soluzione SharePoint, si importa la soluzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e quindi si distribuisce la soluzione nello stesso sito da cui è stata esportata, la soluzione originale di SharePoint viene sostituita. Questo problema non si verifica se si distribuisce la soluzione in un server in cui non è attivata la soluzione originale.

### <a name="error-message"></a>Messaggio di errore
 Nessuna.

### <a name="resolution"></a>Risoluzione
 Per evitare di sovrascrivere una soluzione nel sito da cui è stata esportata, modificare i GUID di SolutionID e gli ID funzionalità di tutte le funzionalità importate nel progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="error-appears-when-debugging-starts"></a>Errore visualizzato all'avvio del debug
 Quando si avvia il debug di una soluzione SharePoint in Visual Studio, viene visualizzato un errore indicante che è impossibile caricare il file di configurazione Web.config in Visual Studio perché la chiave specificata non è presente nel dizionario.

### <a name="error-message"></a>Messaggio di errore
 Impossibile caricare il file di configurazione Web. config. Controllare il file per individuare eventuali elementi XML non validi e riprovare. Si è verificato l'errore seguente: la chiave specificata non è presente nel dizionario.

### <a name="resolution"></a>Risoluzione
 Per risolvere questo problema, verificare che il valore della proprietà URL sito del progetto SharePoint in Visual Studio corrisponda all'URL assegnato all'area predefinita per i mapping di accesso alternativo dell'applicazione Web. L'utilizzo di un'altra area, ad esempio Intranet, per l'URL non risolverà l'errore. L'URL del sito del progetto e l'URL nell'area predefinita devono corrispondere. Per accedere ai mapping di accesso alternativo, aprire l'utilità Amministrazione centrale SharePoint 2010, scegliere il collegamento **Gestione applicazioni** e quindi, in **applicazioni Web**, scegliere il collegamento **Configura mapping di accesso alternativo** . Per altre informazioni, vedere [creare zone per le applicazioni Web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Vedere anche

- [Risolvere i problemi di distribuzione e creazione di pacchetti di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debug in Visual Studio](../debugger/debugger-feature-tour.md)