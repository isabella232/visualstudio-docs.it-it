---
title: Risoluzione dei problemi relativi alla creazione e alla distribuzione di SharePoint | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eafac8015b7a2c51279b7a2d664f0e094d2397b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981929"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Risolvere i problemi di distribuzione e creazione di pacchetti di SharePoint
  In questo argomento vengono analizzati vari problemi che possono verificarsi durante la creazione di pacchetti e la distribuzione di soluzioni SharePoint.

## <a name="enable-enhanced-debugging"></a>Abilita debug avanzato
 Per effettuare una diagnosi dei problemi relativi a Visual Studio, SharePoint e ad altri livelli, è possibile utilizzare la chiave del Registro di sistema EnableDiagnostics per visualizzare la traccia dello stack. Per ulteriori informazioni, vedere [debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Aggiungere l'output del progetto al pacchetto della soluzione
 È possibile aggiungere l'output del progetto a un pacchetto mediante Progettazione pacchetti. Quando tuttavia si aggiunge l'output del progetto, verificare che la piattaforma del progetto corrisponda alla piattaforma della soluzione SharePoint. Si consiglia di utilizzare la destinazione **qualsiasi piattaforma CPU** per gli assembly che si desidera distribuire in un server SharePoint. Per ulteriori informazioni, vedere la pagina relativa alla [compilazione, Progettazione progetti &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) e la finestra di [dialogo impostazioni del compilatore avanzate &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Avvisi ed errori di convalida
 Gli strumenti di sviluppo di SharePoint in Visual Studio consentono di eseguire passi di convalida per verificare che il pacchetto della soluzione venga creato correttamente. È inoltre possibile creare passi di convalida personalizzati per le funzionalità e i pacchetti. Per altre informazioni, vedere [procedura: creare regole personalizzate per la convalida di funzionalità e pacchetti per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Risoluzione dei conflitti di distribuzione
 Quando si distribuisce una soluzione SharePoint, possono verificarsi conflitti se un elemento sul server ha lo stesso nome, URL o ID di un elemento presente nel pacchetto della soluzione. È possibile modificare la proprietà **risoluzione conflitti di distribuzione** per risolvere, segnalare o ignorare i conflitti per moduli, Web part, istanze di elenco e tipi di contenuto.

 Nella tabella seguente vengono illustrate le impostazioni per la proprietà di **risoluzione dei conflitti di distribuzione** .

|Valore|Descrizione|
|-----------|-----------------|
|Automatico|I conflitti vengono rilevati e risolti automaticamente.|
|Prompt|I conflitti vengono rilevati e segnalati allo sviluppatore prima di essere risolti.|
|Nessuno|I conflitti non vengono rilevati.|

## <a name="differences-between-f5-deployment"></a>Differenze tra la distribuzione di F5
 Quando si utilizza [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per distribuire il progetto SharePoint nel server SharePoint locale per il test e l'esecuzione del debug, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vengono eseguiti alcuni passaggi aggiuntivi.

1. Reimpostazione di Internet Information Service (IIS) durante il passaggio di distribuzione.

2. Associazione automatica dei flussi di lavoro.

3. Impostazione dell'ordine di attivazione delle funzionalità in base alla gerarchia di Progettazione pacchetti.

   È possibile aggiungere passaggi di distribuzione personalizzati per modificare ulteriormente il comportamento di **F5** . Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Ritardo nella visualizzazione della pagina di SharePoint durante la distribuzione di Web part visiva
 La visualizzazione della pagina di SharePoint richiede molto tempo quando si distribuisce una Web part visiva nella cartella Bin di [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] o [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Se si modificano i file di una directory di livello superiore di [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], ad esempio la directory Bin, viene ricompilata l'intera applicazione Web. Questo può determinare fino a 25 secondi di ritardo nel rendering della pagina di SharePoint.

### <a name="error-message"></a>Messaggio di errore
 Nessuno.

### <a name="resolution"></a>Soluzione
 Per risolvere il problema, effettuare i passaggi seguenti:

1. Installare l'aggiornamento KB967535 come illustrato nell'articolo relativo alla correzione dell'articolo supporto tecnico Microsoft [: è disponibile un hotfix per risolvere due problemi in ASP.NET in IIS 7,0 per Windows Vista e Windows Server 2008](https://support.microsoft.com/help/967535).

2. Aggiungere la riga di codice seguente al file Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>La distribuzione del progetto SharePoint non riesce con errore "Impossibile estrarre il file CAB nella soluzione"
 Se il nome di un qualsiasi elemento di progetto SharePoint contiene parentesi, la distribuzione della soluzione non riesce generando un errore.

### <a name="error-message"></a>Messaggio di errore
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Impossibile estrarre il file cab nella soluzione.

### <a name="resolution"></a>Soluzione
 Per risolvere il problema, rimuovere le parentesi nei nomi degli elementi di progetto SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Viene visualizzato un errore durante la distribuzione di una Web part visiva in un sito in un'altra applicazione Web
 La prima volta che viene distribuita una Web part visiva a un sito su un'applicazione Web diversa da quella sulla quale è correntemente distribuita (modificando la proprietà SiteUrl della Web part visiva), si ottiene un errore.

### <a name="error-message"></a>Messaggio di errore
 Si è verificato un errore nel passaggio di distribuzione 'Aggiungi Soluzione': Una funzionalità con ID [#] è già stata installata in questa farm. Utilizzare l'attributo force per installare nuovamente in modo esplicito la funzionalità.

### <a name="resolution"></a>Soluzione
 Questo errore si verifica a causa della modalità con cui le funzionalità della Web part visiva vengono ritratte in SharePoint. Per distribuire correttamente la Web part visiva, distribuire di nuovo la soluzione scegliendo il tasto **F5** .

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Avviso visualizzato durante la distribuzione di controlli utente annidati
 Questo avviso viene visualizzato quando si distribuisce una soluzione SharePoint in cui sono annidati controlli utente, quale una web part visiva contenente un controllo utente o un controllo utente contenente una web part visiva o un altro controllo utente. Questo avviso viene visualizzato se si aggiunge un controllo a una finestra di progettazione trascinandoli dalla casella degli strumenti o usando la @Register direttiva nella visualizzazione origine.

### <a name="error-message"></a>Messaggio di errore
 Avviso 1 l'elemento ' [*nome controllo*]' non è un elemento noto. Il problema potrebbe essere dovuto a un errore di compilazione del sito Web oppure il file web.config risulta mancante.

### <a name="resolution"></a>Soluzione
 Se il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sistema del progetto non è a conoscenza di un controllo utente annidato, non può fornire IntelliSense e genera l'avviso. Il sistema del progetto non riconosce un controllo utente annidato se il progetto non viene compilato e la finestra di progettazione non viene chiusa né riaperta oppure se l'opzione di ritrazione automatica è abilitata, causando la ritrazione del controllo utente dall'hive SharePoint dopo il debug.

 Per rimuovere questo avviso, compilare il progetto, quindi chiudere e riaprire la finestra di progettazione oppure disabilitare l'opzione di ritrazione automatica per il progetto. A tale scopo, deselezionare la casella di controllo **ritrazione automatica dopo il debug** nella scheda **SharePoint** della finestra di dialogo Proprietà progetto.

## <a name="see-also"></a>Vedere anche

- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)