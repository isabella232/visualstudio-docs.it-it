---
title: Risoluzione dei problemi delle soluzioni SharePoint | Microsoft Docs
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
ms.openlocfilehash: bab7f45824def7a4b5a385381a4789b7adc276d0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048619"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Risolvere i problemi di soluzioni SharePoint
  Potrebbero verificarsi i problemi o gli avvisi seguenti durante il debug di soluzioni SharePoint tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger. Per altre informazioni, vedere [debug delle soluzioni di flusso di lavoro di SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrizioni dei token nelle sandbox web part visive
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

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrizioni dei caratteri nei nomi di progetti ed elementi di progetto
 Nei nomi di progetti e di elementi di progetto possono essere inclusi solo caratteri che sono validi in un percorso di distribuzione in SharePoint 2010. Altri caratteri non sono consentiti.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "Caratteri non validi".

### <a name="resolution"></a>Risoluzione
 Per i nomi di progetti e di elementi di progetto di SharePoint, utilizzare solo i caratteri seguenti:

- Caratteri ASCII alfanumerici

- Spazio

- Punto (.)

- Virgola ()

- Carattere di sottolineatura (_)

- Dash (-)

- Barra rovesciata (\\)

  Quando viene creato un pacchetto di un progetto, tramite una regola di convalida viene verificato che nella proprietà del percorso di distribuzione per ogni file distribuito siano contenuti solo questi caratteri validi.

## <a name="errors-when-creating-custom-fields"></a>Errori durante la creazione di campi personalizzati
 I campi personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono definiti in XML. Si possono verificare errori se un campo non è definito o non vi viene fatto riferimento tramite un formato specifico.

### <a name="error-message"></a>Messaggio di errore
 Messaggio di errore "Caratteri non validi" in fase di creazione dei pacchetti.

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

 Come illustrato nell'esempio seguente, un riferimento di campo in un tipo di contenuto deve essere definito utilizzando il formato di elemento vuoto (\<FieldRef / >), non tramite elementi iniziali o finali (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Se il codice XML di origine per il campo non è corretto, ad esempio un file XML non è valido o presenta altri problemi, si verificherà l'errore indicante che non è possibile analizzare il file.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nuove definizioni del sito non in lingua inglese non sono visualizzate nella pagina di creazione del sito dopo la distribuzione
 Dopo aver creato e distribuire una definizione di sito utilizzando una versione non inglese di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (vale a dire, una versione con le impostazioni locali [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] diverso da 1033), il **personalizzazioni di SharePoint** scheda non viene visualizzato nei **Selezione modello** finestra e il nuovo modello di sito non viene visualizzato nei **nuovo sito di SharePoint** pagina.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica a causa di un valore non corretto nel **tracciato** file di proprietà per la configurazione della definizione sito webtemp, ad esempio *webtemp_SiteDefinitionProject1*. Nel **percorso** proprietà per il file webtemp, che si trova sotto il **percorso di distribuzione**, modificare le impostazioni locali 1033 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ad esempio, per usare le impostazioni locali giapponesi modificare il valore per 1041. Per altre informazioni, vedere [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Errore viene visualizzato quando un progetto di flusso di lavoro viene distribuito in un sistema pulito
 Questo problema si verifica se si distribuisce un progetto flusso di lavoro in un computer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con un sistema pulito. Un sistema pulito è un computer in cui è presente una nuova installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di SharePoint, ma non sono presenti progetti flusso di lavoro distribuiti.

### <a name="error-message"></a>Messaggio di errore
 Impossibile trovare l'elenco di SharePoint: Cronologia del flusso di lavoro.

### <a name="resolution"></a>Risoluzione
 Questo errore si verifica a causa di un elenco Cronologia flussi di lavoro mancano. Poiché l'ambiente di sviluppo è un sistema pulito, alcun flusso di lavoro non viene distribuiti e l'elenco di cronologia del flusso di lavoro non esiste ancora. Per risolvere questo problema, aprire nuovamente la procedura guidata del flusso di lavoro, che fa sì che l'elenco Cronologia flussi di lavoro da creare.

##### <a name="to-reenter-the-workflow-wizard"></a>Immettere nuovamente la procedura guidata del flusso di lavoro

1. Nelle **Esplora soluzioni**, scegliere il nodo del flusso di lavoro.

2. Nel **proprietà** finestra, fare clic sul pulsante con puntini di sospensione (...) su qualsiasi proprietà che dispone di un pulsante con puntini di sospensione.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>L'utente deve aggiornare la pagina dell'applicazione nel browser durante il debug per visualizzare l'immagine aggiornata
 Se si esegue il debug di una soluzione di SharePoint contenente una pagina dell'applicazione con un controllo che visualizza un'immagine, ad esempio un [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] controllo immagine, è necessario aggiornare la pagina nel browser per visualizzare tutte le modifiche apportate all'immagine.

## <a name="error-the-site-location-is-not-valid"></a>Errore: Il percorso del sito non è valido
 Questo problema può verificarsi se [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] non è installato. Si potrebbe verificare anche se non hai accesso come amministratore al sito Web di SharePoint specificato nella **Personalizzazione guidata SharePoint**.

### <a name="error-message"></a>Messaggio di errore

- Percorso di sito di SharePoint non è valido.

### <a name="resolution"></a>Risoluzione

- Installare [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Assicurarsi di avere accesso di amministratore per il sito Web di SharePoint. Per altre informazioni, vedere la [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] articolo in linea [assegnare o rimuovere gli amministratori di applicazioni di servizio in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Eventi web eliminazione sito non si verificano nel progetto ricevitore di eventi
 Quando si crea un progetto di ricevitore di eventi e si selezionano determinati eventi Web, ad esempio "un sito di eliminazione in corso", l'evento si verifica mai.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Questo problema si verifica perché l'ambito della funzionalità deve essere "Sito" per gestire gli eventi a livello di sito, ma l'ambito della funzionalità predefinita per i progetti di ricevitore di eventi è "Web". Gli eventi Web interessati sono:

- Un sito viene eliminato (WebDeleting)

- Un sito è stato eliminato (WebDeleted)

- Un sito viene spostato (WebMoving)

- È stato spostato un sito (WebMoved)

  Per risolvere il problema, modificare l'ambito di funzionalità del ricevitore di eventi, come indicato di seguito.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Per modificare l'ambito di funzionalità del ricevitore di eventi

1. Nelle **Esplora soluzioni**, aprire il ricevitore di eventi *feature* del file nei **Progettazione funzionalità** doppio clic sul file o aprendo il relativo menu di scelta rapida e quindi scelta **aperto**.

2. Scegliere la freccia accanto a **ambito**, quindi scegliere **sito** nell'elenco visualizzato.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Errore di distribuzione viene visualizzato dopo aver modificato il nome di un identificatore in un progetto modello di connettività dei dati
 Questo problema si verifica se si modifica il nome dell'identificatore di un'entità in un modello di integrazione applicativa dei dati (BDC) e quindi provare a distribuire la soluzione.

### <a name="error-messages"></a>Messaggi di errore

- \<*nome del modello*> presenta i seguenti errori di attivazione di tipo di contenuto esterno...

- IMetadataObject denominato '\<*nome del modello*>' ha un valore nel campo 'name' che è duplicato...

### <a name="resolution"></a>Risoluzione
 Per risolvere questo problema, eliminare manualmente il modello e quindi distribuire nuovamente la soluzione.  È possibile eliminare il modello usando uno dei seguenti strumenti:

- Amministrazione centrale SharePoint 2010. Per altre informazioni, vedere [modelli BDC](http://go.microsoft.com/fwlink/?LinkID=181472) nel sito Web Microsoft TechNet.

- Windows PowerShell. È possibile eliminare il modello digitando questo comando al prompt dei comandi: **Remove-SPBusinessDataCatalogModel**. Per altre informazioni, vedere [cmdlet generali (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) nel sito Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Viene visualizzato un errore quando si prova a visualizzare una web part visiva in SharePoint
 Questo problema si verifica quando la **tracciato** proprietà del controllo utente non inizia con la stringa "CONTROLTEMPLATES\\".

### <a name="error-messages"></a>Messaggi di errore

- Il file "/_CONTROLTEMPLATES/*\<nome progetto >*/*\<nome della Web Part >*/*\<controllo utente nome >*. ascx "non esiste.

- Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione

##### <a name="to-resolve-this-issue"></a>Per risolvere il problema

1. Nelle **Esplora soluzioni**, scegliere il file di controllo utente, la cui estensione viene *ascx*.

2. Nella barra dei menu, scegliere **View** > **finestra proprietà**.

3. Nel **delle proprietà** finestra, espandere il **percorso di distribuzione** nodo.

4. Assicurarsi che il valore della **tracciato** proprietà inizia con la stringa "CONTROLTEMPLATES\\".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Errore viene visualizzato quando si esegue un flusso di lavoro riutilizzabile importato che contiene un campo del form attività
 Questo problema si verifica se si importa un flusso di lavoro che contiene un modulo di attività che dispone di un campo e quindi esecuzione di nuovo flusso di lavoro nello stesso sistema da cui è stato importato.

### <a name="error-message"></a>Messaggio di errore
 Errore durante il passaggio di distribuzione attiva funzionalità: Il campo con Id [*Guid*] definito in funzionalità [*Guid*] è stato trovato nella raccolta di siti corrente o in un sito secondario.

### <a name="resolution"></a>Risoluzione
 Questo errore è il risultato di collisioni ID campo che si verificano poiché il flusso di lavoro riutilizzabile di importazione del progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non modifica campo del form attività ID. Se si distribuisce un flusso di lavoro importato nello stesso server che contiene il flusso di lavoro originale, si verifica conflitti tra ID di campo.

 Per risolvere questo problema, usare la funzionalità di ricerca e sostituzione per modificare il valore dell'attributo campo ID in tutti i file di flusso di lavoro importato.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Errore viene visualizzato quando un rinominato importati viene eseguita l'istanza di elenco
 Questo problema si verifica se si rinomina un'istanza di elenco importata e quindi eseguirlo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Messaggio di errore
 Errore di compilazione: Errore durante il passaggio di distribuzione attiva funzionalità: Il file Template\Features\\[*Importa progetto*<em>caratteristica</em>*nome*] \Files\Lists\\[*precedente* <em>nome elenco</em>] \Schema.xml non esiste.

### <a name="resolution"></a>Risoluzione
 Quando si importa un'istanza di elenco, un attributo denominato CustomSchema viene aggiunto al file Elements. XML dell'istanza di elenco. Elements. XML include il percorso di un file schema. XML personalizzato per l'istanza di elenco. Quando si rinomina l'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene modificato il percorso di distribuzione per il file schema. XML personalizzato, ma il valore di percorso dell'attributo CustomSchema non viene aggiornato. Di conseguenza, l'istanza di elenco non è stato trovato il *schema* file nel vecchio percorso specificato dall'attributo CustomSchema quando la funzionalità viene attivata.

 Per risolvere questo problema, aggiornare il percorso della posizione di distribuzione di *schema* file nell'attributo CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint terminata da IIS la sessione di debug
 Questo problema si verifica se si imposta un punto di interruzione in un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] soluzione di SharePoint, scegliere il **F5** tasto per eseguire il file e quindi restare in corrispondenza di un punto di interruzione più di 90 secondi.

### <a name="error-message"></a>Messaggio di errore
 Il processo del server Web in fase di debug è stato terminato da Internet Information Services (IIS). Il problema può essere risolto configurando le impostazioni ping del pool di applicazioni in IIS. Vedere la Guida per altri dettagli.

### <a name="resolution"></a>Risoluzione
 Per impostazione predefinita, il pool di applicazioni IIS attende 90 secondi per un'applicazione di rispondere prima della chiusura dell'applicazione. Questo processo è noto come "ping" l'applicazione. Per risolvere questo problema, è possibile aumentare il tempo di attesa o disabilitare completamente il ping dell'applicazione.

##### <a name="to-access-the-iis-app-pool-settings"></a>Per accedere alle impostazioni di IIS app pool

1. Aprire Gestione IIS.

2. Nel **connessioni** riquadro, espandere il nodo del server SharePoint e quindi scegliere il **pool di applicazioni** nodo.

3. Nel **pool di applicazioni** pagina, scegliere il pool di applicazioni di SharePoint (in genere "SharePoint - 80") e quindi nel **azioni** riquadro, scegliere il **impostazioni avanzate** collegamento.

4. Per aumentare il tempo di attesa prima del timeout IIS, modificare il valore della **tempo di risposta massimo Ping (secondi)** su un valore maggiore di 90 secondi.

5. Per disabilitare il ping di IIS, impostare **Ping abilitato** al **False**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Ritrazione automatica lascia l'istanza di elenco orfani in SharePoint
 Questo problema si verifica se si esegue la procedura seguente.

1. Creare una definizione di elenco con un'istanza di elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Scegliere il **F5** tasto per eseguire la soluzione.

3. Arrestare il debug oppure chiudere il sito di SharePoint.

4. Riaprire il sito di SharePoint e aprire l'istanza di elenco.

### <a name="error-message"></a>Messaggio di errore
 Errore del server nell'applicazione '/'.

### <a name="resolution"></a>Risoluzione
 Ciò accade perché dopo la chiusura di una sessione di debug di una soluzione di SharePoint, la ritrazione automatica funzionalità ritrae la soluzione. Il ritiro della Elimina la definizione di elenco da SharePoint, ma non l'istanza dell'elenco. La definizione di elenco sottostante è obbligatoria per l'istanza di elenco.

 Per risolvere questo problema, distribuire la soluzione, nella barra dei menu, scegliendo **compilare** > **Distribuisci**. (Non eseguire il debug della soluzione, scegliere il **F5** chiave.) Quindi, eliminare l'istanza di elenco in SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Soluzione di SharePoint originale viene sostituita da una versione esportata
 Se si esporta una soluzione di SharePoint, Importa la soluzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e quindi distribuire la soluzione nuovamente allo stesso sito da cui è stato esportato, la soluzione di SharePoint originale viene sostituita. Questo problema si verifica se si distribuisce la soluzione in un server che non è la soluzione originale attivata su di esso.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Risoluzione
 Per evitare la sovrascrittura di una soluzione nel sito da cui è stato esportato, cambiare i GUID degli SolutionID e gli ID di funzionalità di tutte le funzionalità importate nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto.

## <a name="error-appears-when-debugging-starts"></a>Errore viene visualizzato all'avvio del debug
 Quando si avvia il debug di una soluzione SharePoint in Visual Studio, viene visualizzato un errore indicante che è impossibile caricare il file di configurazione Web.config in Visual Studio perché la chiave specificata non è presente nel dizionario.

### <a name="error-message"></a>Messaggio di errore
 Impossibile caricare il file di configurazione Web. config. Controllare il file per tutti gli elementi XML in formato non corretto e ripetere l'operazione. Si è verificato il seguente errore: La chiave specificata non è presente nel dizionario.

### <a name="resolution"></a>Risoluzione
 Per risolvere questo problema, verificare che il valore della proprietà URL sito del progetto SharePoint in Visual Studio corrisponda all'URL assegnato all'area predefinita per i mapping di accesso alternativo dell'applicazione Web. L'utilizzo di un'altra area, ad esempio Intranet, per l'URL non risolverà l'errore. L'URL del sito del progetto e l'URL nell'area predefinita devono corrispondere. Per accedere ai mapping di accesso alternativo, aprire l'utilità di amministrazione centrale SharePoint 2010, scegliere il **Gestione applicazioni** collegamento e quindi selezionare **applicazioni Web**, scegliere il  **Configura mapping di accesso alternativo** collegamento. Per altre informazioni, vedere [creare le zone per le applicazioni Web](http://go.microsoft.com/fwlink/?LinkId=192274).

## <a name="see-also"></a>Vedere anche

- [Risolvere i problemi di distribuzione e la creazione di pacchetti di SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)