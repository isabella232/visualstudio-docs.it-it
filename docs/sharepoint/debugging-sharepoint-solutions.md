---
title: Debug SharePoint soluzioni | Microsoft Docs
description: Eseguire SharePoint le soluzioni usando il debugger Visual Studio. Esplorare il processo di debug e distribuzione F5, i flussi di lavoro di debug e i ricevitori di eventi delle funzionalità di debug.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 13b486f9975c6a8f42c638b1a2eac0f84c373bba22a003dc0dbf3f108e4fa2da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425570"
---
# <a name="debug-sharepoint-solutions"></a>Eseguire il debug SharePoint soluzioni
  È possibile eseguire il debug SharePoint soluzioni personalizzate usando il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger. Quando si avvia il debug, distribuisce i file di progetto nel server SharePoint e quindi apre un'istanza del sito SharePoint nel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web browser. Le sezioni seguenti illustrano come eseguire il debug SharePoint applicazioni in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Abilitare il debug](#enable-debugging)

- [Processo di debug e distribuzione F5](#f5-debug-and-deployment-process)

- [SharePoint funzionalità del progetto](#sharepoint-project-features)

- [Flussi di lavoro di debug](#debug-workflows)

- [Ricevitori di eventi di funzionalità di debug](#debug-feature-event-receivers)

- [Abilitare le informazioni di debug con ehanced](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Abilitare il debug
 Quando si esegue per la prima volta il debug di una soluzione SharePoint in , viene visualizzata una finestra di dialogo che segnala che il file web.config non è configurato per abilitare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il debug. Il file web.config viene creato quando si installa SharePoint server. Per altre informazioni, vedere [Uso di Web.config file](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)). La finestra di dialogo consente di eseguire il progetto senza eseguire il debug o di modificare il file web.config per abilitare il debug. Se si sceglie la prima opzione, il progetto viene eseguito normalmente. Se si sceglie la seconda opzione, il file web.config viene configurato per:

- Attivare lo stack di chiamate ( `CallStack="true"` )

- Disabilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Abilitare il debug della compilazione ( `<compilation debug="true">` )

  Il file web.config seguente:

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

 Per invertire le modifiche e disabilitare il debug, modificare quanto segue nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file web.config:

- Disattivare lo stack di chiamate ( `CallStack="false"` )

- Abilitare gli errori personalizzati in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Disabilitare il debug della compilazione ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>Processo di debug e distribuzione F5
 Quando si esegue il progetto SharePoint in modalità di debug, il SharePoint di distribuzione esegue le attività seguenti:

1. Esegue i comandi di pre-distribuzione personalizzabili.

2. Crea un file di pacchetto della soluzione Web (con estensione wsp) usando [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] i comandi . Il file con estensione wsp include tutti i file e le funzionalità necessari. Per altre informazioni, vedere [Panoramica delle soluzioni](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Se la SharePoint soluzione è una soluzione farm, ricicla il [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni per il sito [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] specificato. Questo passaggio rilascia i file bloccati dal [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] processo di lavoro.

4. Se esiste già una versione precedente del pacchetto, ritira la versione precedente delle funzionalità e dei file nel file con estensione wsp. Questo passaggio disattiva le funzionalità, disinstalla il pacchetto della soluzione e quindi elimina il pacchetto della soluzione SharePoint server.

5. Installa la versione corrente delle funzionalità e dei file nel file con estensione wsp. Questo passaggio aggiunge e installa la soluzione nel server SharePoint server.

6. Per i flussi di lavoro, installa l'assembly del flusso di lavoro. È possibile modificarne il percorso usando la *proprietà Percorso assembly.*

7. Attiva la funzionalità del progetto in SharePoint se l'ambito è Sito o Web. Le funzionalità negli ambiti Farm e WebApplication non sono attivate.

8. Per i flussi di lavoro, associa il flusso di lavoro SharePoint raccolta, elenco o sito selezionato nella SharePoint **personalizzazione guidata**.

   > [!NOTE]
   > Questa associazione si verifica solo se è stata selezionata **l'opzione Associa automaticamente flusso di lavoro** nella procedura guidata.

9. Esegue i comandi personalizzabili post-distribuzione.

10. Collega il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger al processo ( [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] *w3wp.exe*). Se il tipo di progetto consente di modificare la proprietà *Soluzione* in modalità sandbox e il relativo valore è impostato su **true,** il debugger si connette a un processo diverso (*SPUCWorkerProcess.exe*). Per altre informazioni, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

11. Avvia il debugger JavaScript se la soluzione SharePoint è una soluzione farm.

12. Visualizza la raccolta, l'elenco o la pagina del sito appropriata nel Web browser.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] visualizza un messaggio di stato nella finestra Output dopo il completamento di ogni attività. Se non è possibile completare un'attività, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] visualizza un messaggio di errore nella finestra Elenco errori.

## <a name="sharepoint-project-features"></a>SharePoint funzionalità del progetto
 Una funzionalità è un'unità di funzionalità portabile e modulare che semplifica la modifica dei siti tramite le definizioni di sito. È anche un pacchetto di elementi (WSS) che possono essere attivati per un ambito specifico e che consentono agli utenti di [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] raggiungere un obiettivo o un'attività specifica. I modelli vengono distribuiti come funzionalità.

 Quando si esegue un progetto in modalità di debug, il processo di distribuzione crea una cartella nella *directory* delle funzionalità in *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. I nomi delle funzionalità hanno il formato nome *progetto* _Feature *x*, ad esempio TestProject_Feature1.

 La cartella della soluzione nella directory delle funzionalità contiene un file di *definizione* della funzionalità e un file di definizione *del flusso di lavoro.* Il file di definizione della funzionalità (Feature.xml) descrive i file nel file feature del progetto. Il file di definizione del progetto (*Elements.xml*) descrive il modello di progetto. *Elements.xml* disponibile **in** Esplora soluzioni , ma Feature.xml viene generato quando viene creato il pacchetto della soluzione. Per altre informazioni su questi file, vedere modelli di SharePoint [progetto e di elemento di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Flussi di lavoro di debug
 Quando si esegue il debug di progetti flusso di lavoro, aggiunge il modello di flusso di lavoro (a seconda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del tipo) a una libreria o a un elenco. È quindi possibile avviare il modello di flusso di lavoro manualmente o aggiungendo o aggiornando un elemento. È quindi possibile usare per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eseguire il debug del flusso di lavoro.

> [!NOTE]
> Se si aggiungono riferimenti ad altri assembly, assicurarsi che tali assembly siano installati nella Global Assembly Cache ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). In caso contrario, la soluzione del flusso di lavoro avrà esito negativo. Per informazioni su come installare gli assembly, vedere Avviare manualmente un [flusso di lavoro in un documento o in un elemento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Tuttavia, il processo di distribuzione non avvia il flusso di lavoro. È necessario avviare il flusso di lavoro dal SharePoint Web. È anche possibile avviare il flusso di lavoro usando un'applicazione client come Microsoft Office Word 2010 o codice lato server separato. Usare uno degli approcci specificati nella **Personalizzazione guidata SharePoint.**

 Ad esempio, se è stato specificato che il flusso di lavoro può essere avviato manualmente, avviare il flusso di lavoro direttamente dall'elemento nella libreria o nell'elenco. Per altre informazioni su come avviare manualmente un flusso di lavoro, vedere Avviare manualmente un [flusso di lavoro in un elemento del documento.](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)

## <a name="debug-feature-event-receivers"></a>Ricevitori di eventi di funzionalità di debug
 Per impostazione predefinita, quando si esegue un'SharePoint, le relative funzionalità vengono attivate automaticamente [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nel server SharePoint. Tuttavia, ciò causa problemi quando si esegue il debug di ricevitori di eventi di funzionalità, perché quando una funzionalità viene attivata da , viene eseguita in un processo diverso [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rispetto al debugger. Ciò significa che alcune funzionalità di debug, ad esempio i punti di interruzione, non funzioneranno correttamente.

 Per disabilitare l'attivazione automatica della funzionalità in SharePoint e consentire il debug corretto dei ricevitori di  eventi delle funzionalità, impostare il valore della proprietà **Configurazione** distribuzione attiva del progetto su Nessuna attivazione prima del debug. Successivamente, dopo aver avviato il debug dell'applicazione SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], attivare manualmente la funzionalità in SharePoint. Per attivare la funzionalità, aprire il **menu** Azioni sito in SharePoint, scegliere  Impostazioni **sito,** scegliere il  collegamento Gestisci funzionalità sito e quindi scegliere il pulsante Attiva accanto alla funzionalità per continuare il debug come di consueto.

## <a name="enable-enhanced-debugging-information"></a>Abilitare le informazioni di debug avanzate
 A causa delle interazioni talvolta complesse tra il processo (devenv.exe), il processo host SharePoint (vssphost4.exe), SharePoint e il livello WCF, la diagnosi degli errori che si verificano durante la compilazione, la distribuzione e così via può essere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] una sfida.** Per risolvere questi errori, è possibile abilitare informazioni di debug avanzate. A tale scopo, passare alla chiave del Registro di sistema seguente nel Registro Windows registro:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Se il valore REG_DWORD "EnableDiagnostics"  non esiste già, crearlo manualmente. Impostare il valore "EnableDiagnostics" su "1".

 Se si imposta questo valore di chiave su 1, le informazioni di analisi dello stack vengono visualizzate nella finestra **Output** ogni volta che si verificano errori del sistema del progetto durante l'esecuzione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per disabilitare le informazioni di debug avanzate, impostare EnableDiagnostics di nuovo su 0 oppure eliminare il valore.

 Per altre informazioni sulle altre chiavi SharePoint del Registro di sistema, vedere Eseguire il debug delle estensioni per gli strumenti SharePoint [in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Risolvere i SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md)
