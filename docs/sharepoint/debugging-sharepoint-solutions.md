---
title: Debug delle soluzioni SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57133b97ede20c0ed28eecbec6e3cea964f9558a
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873110"
---
# <a name="debug-sharepoint-solutions"></a>Il debug delle soluzioni SharePoint
  È possibile eseguire il debug di soluzioni SharePoint tramite il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger. Quando si avvia il debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce i file di progetto nel server SharePoint e quindi apre un'istanza del sito di SharePoint nel Web browser. Le sezioni seguenti illustrano come eseguire il debug di applicazioni di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

-   [Abilitare il debug](#enable-debugging)

-   [Processo di distribuzione e debug F5](#f5-debug-and-deployment-process)

-   [Funzionalità del progetto SharePoint](#sharepoint-project-features)

-   [Eseguire il debug dei flussi di lavoro](#debug-workflows)

-   [Eseguire il debug di ricevitori di eventi](#debug-feature-event-receivers)

-   [Abilitare ehanced le informazioni di debug](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Abilita debug
 Durante il debug prima di tutto una soluzione di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], una finestra di dialogo avvisa l'utente che il file Web. config non è configurato per abilitare il debug. (Il file Web. config viene creato quando si installa SharePoint server. Per altre informazioni, vedere [uso di file Web. config](http://go.microsoft.com/fwlink/?LinkID=149266).) La finestra di dialogo offre la possibilità di scegliere se eseguire il progetto senza debug oppure modificare il file Web. config per abilitare il debug. Se si sceglie la prima opzione, il progetto viene eseguito normalmente. Se si sceglie la seconda opzione, il file web.config viene configurato per:

- Attivare lo stack di chiamate (`CallStack="true"`)

- Disabilitare gli errori personalizzati nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- Abilitare il debug di compilazione (`<compilation debug="true">`)

  Il file Web. config risultante seguente:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Per annullare le modifiche e disabilitare il debug, modificare gli elementi seguenti [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] nel file Web. config:

-   Disattivare lo stack di chiamate (`CallStack="false"`)

-   Abilitare errori personalizzati nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

-   Disabilitare il debug di compilazione (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>Processo di distribuzione e debug F5
 Quando si esegue il progetto SharePoint in modalità di debug, il processo di distribuzione di SharePoint esegue le attività seguenti:

1. Esegue i comandi di pre-distribuzione personalizzabili.

2. Crea un file del pacchetto (con estensione wsp) soluzioni Web utilizzando [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comandi. Il file con estensione wsp include tutti i file necessari e le funzionalità. Per altre informazioni, vedere [panoramica delle soluzioni](http://go.microsoft.com/fwlink/?LinkID=128154).

3. Se la soluzione di SharePoint è una soluzione farm, ricicla le [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni per il sito specificato [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Questo passaggio rilascia i file bloccati dal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo di lavoro.

4. Se esiste già una versione precedente del pacchetto, viene ritratta la versione precedente delle funzionalità e i file nel file con estensione wsp. Questo passaggio per disattivare le funzionalità, disinstalla il pacchetto della soluzione e quindi Elimina il pacchetto della soluzione nel server SharePoint.

5. Installa la versione corrente delle funzionalità e i file nel file con estensione wsp. Questo passaggio aggiunge e installa la soluzione nel server SharePoint.

6. Per i flussi di lavoro, installa l'assembly del flusso di lavoro. È possibile modificare il percorso usando il *percorso dell'Assembly* proprietà.

7. Attiva funzionalità del progetto SharePoint se l'ambito è siti o Web. Funzionalità negli ambiti WebApplication e Farm non sono attivate.

8. Per i flussi di lavoro, consente di associare il flusso di lavoro con la libreria, elenco o sito selezionato in SharePoint le **Personalizzazione guidata SharePoint**.

   > [!NOTE]
   >  Questa associazione viene generato solo se è stato selezionato **associa automaticamente flussi di lavoro** nella procedura guidata.

9. Esegue i comandi di post-distribuzione personalizzabili.

10. Collega il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del debugger per il [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] processo (*w3wp.exe*). Se il tipo di progetto consente di modificare la *soluzione creata mediante sandbox* e il relativo valore è impostato su **true**, il debugger viene connesso a un altro processo (*SPUCWorkerProcess.exe*). Per altre informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

11. Avvia il debugger JavaScript se la soluzione di SharePoint è una soluzione farm.

12. Consente di visualizzare la libreria appropriata, un elenco o una pagina del sito nel Web browser.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di stato nella finestra di Output dopo ogni attività è stata completata. Se non è possibile completare un'attività, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di errore nella finestra Elenco errori.

## <a name="sharepoint-project-features"></a>Funzionalità del progetto SharePoint
 Una funzionalità è un'unità modulare e portatile di funzionalità che semplificano la modifica dei siti usando definizioni di sito. È anche un pacchetto di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] elementi (WSS) che possono essere attivati per un ambito specifico e che consente agli utenti di eseguire un'attività o un obiettivo specifico. I modelli vengono distribuiti come funzioni.

 Quando si esegue un progetto in modalità di debug, il processo di distribuzione crea una cartella nel *caratteristica* directory alla *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. I nomi delle funzionalità hanno il formato *nome progetto*feature*x*, ad esempio TestProject_Feature1.

 La cartella della soluzione nella directory funzionalità contiene un *definizione della caratteristica* file e un *definizione flusso di lavoro* file. Il file di definizione di funzionalità (feature. XML) descrive i file nel file di definizione del progetto indicato nel progetto (*Elements*) descrive il modello di progetto. *Elements. XML* reperibili nel **Esplora soluzioni**, ma feature. XML viene generato quando viene creato il pacchetto della soluzione. Per altre informazioni su questi file, vedere [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Flussi di lavoro di debug
 Quando si esegue il debug di progetti di flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il modello di flusso di lavoro (a seconda del tipo) a una raccolta o a un elenco. È quindi possibile avviare il modello di flusso di lavoro manualmente o mediante l'aggiunta o aggiornamento di un elemento. È quindi possibile usare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per eseguire il debug del flusso di lavoro.

> [!NOTE]
>  Se si aggiungono i riferimenti ad altri assembly, assicurarsi che tali assembly vengono installati nella global assembly cache ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). In caso contrario, la soluzione del flusso di lavoro avrà esito negativo. Per informazioni su come installare gli assembly, vedere [avviare manualmente un flusso di lavoro su un documento o elemento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Tuttavia, il processo di distribuzione non viene avviato il flusso di lavoro. È necessario avviare il flusso di lavoro dal sito Web di SharePoint. È anche possibile avviare il flusso di lavoro tramite un'applicazione client, ad esempio Microsoft Office Word 2010 o tramite codice lato server separato. Usare uno degli approcci specificati nella **Personalizzazione guidata SharePoint**.

 Ad esempio, se è stato specificato che il flusso di lavoro può essere avviata manualmente, avviare il flusso di lavoro direttamente dall'elemento della libreria o dell'elenco. Per altre informazioni su come avviare manualmente un flusso di lavoro, vedere [avviare manualmente un flusso di lavoro su un elemento documento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Eseguire il debug di ricevitori di eventi
 Per impostazione predefinita, quando si esegue un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazione SharePoint, le relative funzionalità vengono attivate automaticamente per l'utente nel server SharePoint. Tuttavia, ciò causa problemi durante il debug di ricevitori di eventi perché quando una funzionalità viene attivata da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], è in esecuzione in un processo diverso dal debugger. Ciò significa che alcune funzionalità di debug, ad esempio punti di interruzione, non funzionerà correttamente.

 Per disabilitare l'attivazione automatica della funzionalità di SharePoint e consentire il corretto debug di ricevitori di eventi, impostare il valore del progetto **configurazione distribuzione attiva** proprietà **Nessuna attivazione** prima del debug. Successivamente, dopo aver avviato il debug dell'applicazione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], attivare manualmente la funzionalità in SharePoint. Per attivare la funzionalità, aprire il **Azioni sito** dal menu in SharePoint, scegliere **le impostazioni del sito**, scegliere il **Gestisci caratteristiche sito** collegamento e quindi scegliere il **Activate** pulsante accanto alla funzionalità e continuare il debug come di consueto.

## <a name="enable-enhanced-debugging-information"></a>Abilita informazioni di debug avanzate
 A causa a volte risultano complesse delle interazioni tra il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo (devenv.exe), il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] processo host di SharePoint (*vssphost4.exe*), SharePoint e il livello WCF, la diagnosi di errori che si verificano mentre compilazione, distribuzione e così via possono essere una sfida. Per aiutarti a risolvere tali errori, è possibile abilitare le informazioni di debug avanzate. A tale scopo, passare alla chiave del Registro di sistema seguente nel Registro di sistema Windows:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Se la "EnableDiagnostics" **REG_DWORD** valore esiste, crearla manualmente. Impostare il valore "EnableDiagnostics" su "1".

 Impostando questo valore chiave su 1 causa stack le informazioni di vengono visualizzate nella traccia le **Output** finestra ogni volta che si verificano errori di sistema di progetto durante l'esecuzione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per disabilitare le informazioni di debug avanzate, impostare EnableDiagnostics di nuovo su 0 oppure eliminare il valore.

 Per altre informazioni sulle altre chiavi del Registro di sistema di SharePoint, vedere [eseguire il Debug delle estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Risolvere i problemi di soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
