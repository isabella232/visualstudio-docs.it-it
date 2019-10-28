---
title: Debug di soluzioni SharePoint | Microsoft Docs
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
ms.openlocfilehash: d83c8ffd4fe5ebb627b70fa07f010bdc713225dd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984482"
---
# <a name="debug-sharepoint-solutions"></a>Debug di soluzioni SharePoint
  È possibile eseguire il debug di soluzioni SharePoint tramite il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quando si avvia il debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce i file di progetto nel server SharePoint e quindi apre un'istanza del sito di SharePoint nel Web browser. Nelle sezioni seguenti viene illustrato come eseguire il debug di applicazioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Abilita debug](#enable-debugging)

- [F5 processo di debug e distribuzione](#f5-debug-and-deployment-process)

- [Funzionalità di progetto SharePoint](#sharepoint-project-features)

- [Flussi di lavoro di debug](#debug-workflows)

- [Ricevitori di eventi di funzionalità di debug](#debug-feature-event-receivers)

- [Abilita informazioni di debug esaltata](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Abilita debug
 Quando si esegue per la prima volta il debug di una soluzione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene visualizzata una finestra di dialogo che informa che il file Web. config non è configurato per abilitare il debug. Il file Web. config viene creato durante l'installazione di SharePoint Server. Per ulteriori informazioni, vedere [utilizzo dei file Web. config](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)). Nella finestra di dialogo è possibile scegliere di eseguire il progetto senza eseguire il debug o modificare il file Web. config per abilitare il debug. Se si sceglie la prima opzione, il progetto viene eseguito normalmente. Se si sceglie la seconda opzione, il file web.config viene configurato per:

- Attivare lo stack di chiamate (`CallStack="true"`)

- Disabilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)

- Abilita debug compilazione (`<compilation debug="true">`)

  Il file Web. config risultante segue:

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

 Per annullare le modifiche e disabilitare il debug, modificare il [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] seguente nel file Web. config:

- Disattivare lo stack di chiamate (`CallStack="false"`)

- Abilita errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)

- Disabilita debug compilazione (`<compilation debug="false">`)

## <a name="f5-debug-and-deployment-process"></a>F5 processo di debug e distribuzione
 Quando si esegue il progetto SharePoint in modalità di debug, il processo di distribuzione di SharePoint esegue le attività seguenti:

1. Esegue i comandi di pre-distribuzione personalizzabili.

2. Consente di creare un file del pacchetto della soluzione Web (con estensione wsp) utilizzando [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comandi. Il file con estensione wsp include tutti i file e le funzionalità necessari. Per altre informazioni, vedere [Panoramica delle soluzioni](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Se la soluzione SharePoint è una soluzione farm, ricicla il pool di applicazioni [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] per l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]del sito specificato. Questo passaggio rilascia i file bloccati dal processo di lavoro [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].

4. Se una versione precedente del pacchetto esiste già, ritrae la versione precedente delle funzionalità e dei file nel file con estensione wsp. Questo passaggio disattiva le funzionalità, disinstalla il pacchetto della soluzione, quindi Elimina il pacchetto della soluzione nel server SharePoint.

5. Installa la versione corrente delle funzionalità e dei file nel file con estensione wsp. Questo passaggio consente di aggiungere e installare la soluzione sul server SharePoint.

6. Per i flussi di lavoro, installa l'assembly del flusso di lavoro. È possibile modificarne la posizione utilizzando la proprietà *Percorso assembly* .

7. Attiva la funzionalità del progetto in SharePoint se l'ambito è sito o Web. Le funzionalità degli ambiti della farm e dell'applicazione non sono attivate.

8. Per i flussi di lavoro, associa il flusso di lavoro alla raccolta di SharePoint, all'elenco o al sito selezionato nella **procedura guidata di personalizzazione di SharePoint**.

   > [!NOTE]
   > Questa associazione si verifica solo se è stata selezionata l'opzione **associa automaticamente flusso di lavoro** nella procedura guidata.

9. Esegue i comandi di post-distribuzione personalizzabili.

10. Connette il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al processo di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (*w3wp. exe*). Se il tipo di progetto consente di modificare la proprietà della *soluzione creata mediante sandbox* e il relativo valore è impostato su **true**, il debugger si connette a un processo diverso (*SPUCWorkerProcess. exe*). Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

11. Avvia il debugger JavaScript se la soluzione SharePoint è una soluzione farm.

12. Visualizza la libreria, l'elenco o la pagina del sito appropriata nel Web browser.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di stato nella finestra output dopo il completamento di ogni attività. Se non è possibile completare un'attività, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visualizza un messaggio di errore nella finestra di Elenco errori.

## <a name="sharepoint-project-features"></a>Funzionalità di progetto SharePoint
 Una funzionalità è un'unità modulare e portatile che semplifica la modifica dei siti usando le definizioni dei siti. È anche un pacchetto di elementi di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) che può essere attivato per un ambito specifico e che consente agli utenti di realizzare un obiettivo o un'attività specifica. I modelli vengono distribuiti come funzionalità.

 Quando si esegue un progetto in modalità di debug, il processo di distribuzione crea una cartella nella directory della *funzionalità* in *%COMMONPROGRAMFILES%\Microsoft Shared\Web server extensions\14\TEMPLATE\FEATURES*. I nomi delle funzionalità hanno il formato *nome del progetto*_Feature*x*, ad esempio TestProject_Feature1.

 La cartella della soluzione nella directory della funzionalità contiene un file di *definizione delle funzionalità* e un file di *definizione del flusso di lavoro* . Il file di definizione delle funzionalità (feature. Xml) descrive i file della funzionalità del progetto. il file di definizione del progetto (*Elements. XML*) descrive il modello di progetto. *Elements. XML* è disponibile in **Esplora soluzioni**, ma feature. XML viene generato al momento della creazione del pacchetto della soluzione. Per ulteriori informazioni su questi file, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Flussi di lavoro di debug
 Quando si esegue il debug di progetti di flusso di lavoro, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il modello di flusso di lavoro (a seconda del tipo) a una raccolta o a un elenco. È quindi possibile avviare il modello di flusso di lavoro manualmente oppure aggiungendo o aggiornando un elemento. È quindi possibile utilizzare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per eseguire il debug del flusso di lavoro.

> [!NOTE]
> Se si aggiungono riferimenti ad altri assembly, assicurarsi che tali assembly siano installati nella Global Assembly Cache ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). In caso contrario, la soluzione flusso di lavoro avrà esito negativo. Per informazioni su come installare gli assembly, vedere [avviare manualmente un flusso di lavoro in un documento o in un elemento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Tuttavia, il processo di distribuzione non avvia il flusso di lavoro. È necessario avviare il flusso di lavoro dal sito Web di SharePoint. È inoltre possibile avviare il flusso di lavoro tramite un'applicazione client, ad esempio Microsoft Office Word 2010, oppure utilizzando codice lato server separato. Utilizzare uno degli approcci specificati nella **procedura guidata di personalizzazione di SharePoint**.

 Se, ad esempio, è stato specificato che il flusso di lavoro può essere avviato manualmente, avviare il flusso di lavoro direttamente dall'elemento nella raccolta o nell'elenco. Per ulteriori informazioni su come avviare manualmente un flusso di lavoro, vedere [avviare manualmente un flusso di lavoro in un elemento del documento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Ricevitori di eventi di funzionalità di debug
 Per impostazione predefinita, quando si esegue un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] applicazione SharePoint, le relative funzionalità vengono automaticamente attivate nel server SharePoint. Tuttavia, ciò causa problemi durante il debug dei ricevitori di eventi di funzionalità, perché quando una funzionalità viene attivata da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], viene eseguita in un processo diverso rispetto al debugger. Ciò significa che alcune funzionalità di debug, come i punti di interruzione, non funzioneranno correttamente.

 Per disabilitare l'attivazione automatica della funzionalità in SharePoint e consentire il debug corretto dei ricevitori di eventi di funzionalità, impostare il valore della proprietà di **configurazione della distribuzione attiva** del progetto su **Nessuna attivazione** prima del debug. Successivamente, dopo aver avviato il debug dell'applicazione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], attivare manualmente la funzionalità in SharePoint. Per attivare la funzionalità, aprire il menu **Azioni sito** in SharePoint, scegliere **Impostazioni sito**, scegliere il collegamento **Gestisci funzionalità sito** , quindi fare clic sul pulsante **attiva** accanto alla funzionalità per continuare a eseguire il debug come di consueto.

## <a name="enable-enhanced-debugging-information"></a>Abilita informazioni di debug avanzate
 A causa delle interazioni a volte complesse tra il processo di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (devenv. exe), il processo host di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint (*vssphost4. exe*), SharePoint e il livello WCF, la diagnosi degli errori che si verificano durante la compilazione, la distribuzione e così via può essere un sfida. Per facilitare la risoluzione di tali errori, è possibile abilitare le informazioni di debug avanzate. A tale scopo, passare alla seguente chiave del registro di sistema nel registro di sistema di Windows:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Se il valore **REG_DWORD** "EnableDiagnostics" non esiste già, crearlo manualmente. Impostare il valore "EnableDiagnostics" su "1".

 Impostando questo valore di chiave su 1, le informazioni di analisi dello stack vengono visualizzate nella finestra di **output** quando si verificano errori del sistema del progetto durante l'esecuzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per disabilitare le informazioni di debug avanzate, impostare EnableDiagnostics di nuovo su 0 oppure eliminare il valore.

 Per ulteriori informazioni sulle altre chiavi del registro di sistema di SharePoint, vedere [estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Risolvere i problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
