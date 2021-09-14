---
title: Uso dell'agente di raccolta autonomo IntelliTrace | Microsoft Docs
description: Usare l'agente di raccolta autonomo IntelliTrace per raccogliere dati senza installare Visual Studio e senza modificare l'ambiente del sistema di destinazione.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f91f9692ab0cd6c9b8cc4cbaf9cdc44cd4d12ad5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710374"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Uso dell'agente di raccolta autonomo IntelliTrace (C#, Visual Basic)

L' **agente di raccolta autonomo IntelliTrace** consente di raccogliere i dati diagnostici di IntelliTrace per le app nei server di produzione o in altri ambienti senza installare Visual Studio nel computer di destinazione e senza cambiare l'ambiente del sistema di destinazione. L'agente di raccolta autonomo IntelliTrace funziona nelle app Web, SharePoint, WPF e Windows Form. Al termine della raccolta dei dati, eliminare semplicemente l'agente di raccolta per disinstallarlo.

 IntelliTrace in azione: [Raccolta e analisi dei dati IntelliTrace in produzione per il debug (video su Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> È anche possibile raccogliere gli stessi dati IntelliTrace per le app Web e SharePoint in esecuzione nei computer remoti usando **Microsoft Monitoring Agent** in modalità **Trace** .
>
> È possibile raccogliere gli eventi relativi alle prestazioni nei dati IntelliTrace eseguendo l'agente in modalità **Monitor** . La modalità **Monitor** ha un impatto minore sulle prestazioni rispetto alla modalità **Traccia** o all' **IntelliTraccia stand-alone collector**. Microsoft Monitoring Agent non modifica l'ambiente del sistema di destinazione quando viene installato. Vedere [Uso dell'Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).
> L'agente di raccolta autonomo IntelliTrace non supporta gli snapshot di processo.

 **Requisiti**

- .NET Framework 3.5 o versione successiva

- Visual Studio Enterprise (ma non edizioni Professional o Community) in un computer di sviluppo o in un altro computer per aprire i file .iTrace

  > [!NOTE]
  > Assicurarsi di salvare i file di simboli (PDB). Per eseguire il debug con IntelliTrace ed eseguire il codice seguendo un'istruzione alla volta sono necessari i file di origine corrispondenti e i file di simboli. Vedere [Diagnosticare i problemi dopo la distribuzione.](../debugger/diagnose-problems-after-deployment.md)

  **Domande frequenti**

- [Quali app funzionano con l'agente di raccolta?](#WhatApps)

- [Come iniziare?](#GetStarted)

- [Come è possibile ottenere il maggior numero possibile di dati senza rallentare l'applicazione?](#Minimizing)

- [In quali altre posizioni è possibile ottenere i dati IntelliTrace?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> Quali app funzionano con l'agente di raccolta?

- ASP.NET App Web ospitate in Internet Information Services (IIS) versione 7.0, 7.5, 8.0, 12.0 e 16.0

- Applicazioni SharePoint 2010 e SharePoint 2013

- App Windows Presentation Foundation (WPF) e Windows Form.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> Ricerca per categorie iniziare?

1. [Installare l'agente di raccolta](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Impostare autorizzazioni per la directory dell'agente di raccolta](#ConfigurePermissionsRunningCollector)

3. [Installare i cmdlet di PowerShell IntelliTrace per raccogliere dati per le applicazioni Web o le applicazioni di SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [Impostare autorizzazioni per la directory di file con estensione iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Raccogliere i dati da un'applicazione Web o da un'applicazione SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -oppure-

     [Raccogliere i dati da un'app gestita](#BKMK_Collect_Data_from_Executables)

6. [Aprire il file .iTrace in Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Installare l'agente di raccolta

1. Nel server dell'app creare la directory dell'agente di raccolta, ad esempio **C:\IntelliTraceCollector**

2. Ottenere l'agente di raccolta [dall'Area](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019)download [Microsoft, my.visualstudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)o dalla cartella Visual Studio 2013 di installazione di Update 3. [Agente di raccolta IntelliTrace per Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909):

   - **Area download Microsoft** **o my.visualstudio.com**:

     1. Accanto a **IntelliTraceCollector.exe**, scegliere **carica**.

     2. Salvare IntelliTraceCollector.exe nella directory dell'agente di raccolta, ad esempio **C:\IntelliTraceCollector**

     3. Eseguire IntelliTraceCollector.exe. Il file IntelliTraceCollection.cab viene estratto.

        \- - oppure -

   - **Cartella di installazione di Visual Studio**:

     1. Copiare IntelliTraceCollection.cab dalla cartella in cui è installato l'agente di raccolta, ad esempio:

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          oppure, per le versioni precedenti di Visual Studio:

          **.. \Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Inserire IntelliTraceCollection.cab nella directory dell'agente di raccolta, ad esempio: **C:\IntelliTraceCollector**

3. Espandere IntelliTraceCollection.cab:

   1. Nel server dell'app aprire una finestra del prompt dei comandi come amministratore.

   2. Cercare la directory dell'agente di raccolta, ad esempio: **C:\IntelliTraceCollector**

   3. Usare il comando **expand** , incluso il punto (**.**) alla fine, per espandere IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Il punto (**.**) lascia inalterate le sottocartelle che contengono i piani di raccolta localizzati.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> Configurare le autorizzazioni per la directory dell'agente di raccolta

1. Nel server dell'app aprire una finestra del prompt dei comandi come amministratore.

2. Usare il comando di Windows **icacls** per concedere all'amministratore del server le autorizzazioni complete per la directory dell'agente di raccolta. Ad esempio:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Per raccogliere dati per un'app Web o un'applicazione SharePoint:

    1. Concedere alla persona che esegue i cmdlet PowerShell di IntelliTrace le autorizzazioni complete per la directory dell'agente di raccolta.

         Ad esempio:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Concedere al pool di applicazioni per l'app Web o l'applicazione SharePoint le autorizzazioni di lettura ed esecuzione per la directory dell'agente di raccolta.

         Ad esempio:

        - Per un'app Web nel pool **di applicazioni DefaultAppPool:**

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - Per un'applicazione SharePoint nel pool di applicazioni **SharePoint - 80** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a>Installare i cmdlet di PowerShell intelliTrace per raccogliere dati per le app Web o SharePoint applicazioni

1. Nel server dell'app, verificare che PowerShell sia abilitato. Nella maggior parte delle versioni di Windows Server, è possibile aggiungere questa funzionalità nello strumento di amministrazione **Server Manager** .

     ![Aggiunta di PowerShell tramite Server Manager](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. Installare i cmdlet PowerShell di IntelliTrace.

    1. Aprire una finestra di comando di PowerShell come amministratore.

        1. Scegliere **Start**, **Tutti i programmi**, **Accessori**, **Windows PowerShell**.

        2. Scegliere uno dei passaggi seguenti:

            - Nei sistemi operativi a 64 bit, aprire il menu di scelta rapida per **Windows PowerShell**. Scegliere **Esegui come amministratore**.

            - Nei sistemi operativi a 32 bit, aprire il menu di scelta rapida per **Windows PowerShell (x86)**. Scegliere **Esegui come amministratore**.

    2. Nella finestra di comando PowerShell, usare il comando **Import-Module** per importare **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Ad esempio:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Configurare le autorizzazioni per la directory dei file con estensione iTrace

1. Nel server dell'app creare la directory di file .iTrace, ad esempio: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Per evitare il rallentamento dell'app, scegliere una posizione in un disco ad alta velocità locale non troppo attivo.
   >   - I file .iTrace e quelli dell'agente di raccolta possono essere inseriti nella stessa posizione. Tuttavia, se si ha un'app Web o un'applicazione SharePoint, verificare che questa posizione non sia all'interno della directory che ospita l'applicazione.
   >
   > [!IMPORTANT]
   > - Limitare la directory di file .iTrace solo alle identità che devono lavorare con l'agente di raccolta. Un file .iTrace può contenere informazioni riservate, ad esempio dati degli utenti, database, altri percorsi di origine e stringhe di connessione, perché IntelliTrace è in grado di registrare tutti i dati che passano nei parametri del metodo o come valori restituiti.
   >   - Assicurarsi che le persone che possono aprire i file .iTrace dispongano delle autorizzazioni per la visualizzazione dei dati riservati. Usare prudenza quando si condividono file .iTrace. Se è necessario concedere l'accesso ad altri, copiare i file in un percorso condiviso sicuro.

2. Per un'app Web o un'applicazione SharePoint, concedere al pool di applicazioni le autorizzazioni complete per la directory di file .iTrace. È possibile usare il comando Windows **icacls** oppure Esplora risorse (o Esplora file).

    Ad esempio:

   - Per configurare le autorizzazioni con il comando Windows **icacls** :

     - Per un'app Web nel pool **di applicazioni DefaultAppPool:**

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Per un'applicazione SharePoint nel pool di applicazioni **SharePoint - 80** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -oppure-

   - Per configurare le autorizzazioni con Esplora risorse (o Esplora file):

     1. Aprire **Proprietà** per directory di file .iTrace.

     2. Nella scheda **Sicurezza** , scegliere **Modifica**, **Aggiungi**.

     3. Verificare che **Entità di sicurezza predefinite** sia visualizzato nella casella **Selezionare questo tipo di oggetto** . Se non è disponibile, scegliere **Tipi di oggetto** per aggiungerlo.

     4. Verificare che il computer locale sia visualizzato nella casella **Da questo percorso** . Se non è disponibile, scegliere **Percorsi** per modificarlo.

     5. Nella casella **Immettere i nomi degli oggetti da selezionare** aggiungere il pool di applicazioni per l'app Web o l SharePoint app.

     6. Scegliere **Controlla nomi** per risolvere il nome. Scegliere **OK**.

     7. Verificare che il pool di applicazioni abbia il **Controllo completo**.

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a>Raccogliere dati da un'app Web o da un SharePoint app

1. Per avviare la raccolta dei dati, aprire una finestra di comando PowerShell come amministratore, quindi eseguire il comando:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Dopo aver eseguito il comando, digitare **Y** per confermare che si vuole iniziare la raccolta dei dati.

     Ad esempio, per raccogliere i dati da un'applicazione SharePoint nel pool di applicazioni **SharePoint - 80** :

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Nome|Descrizione|
    |-|-|
    |*Pool di applicazioni*|Il nome del pool di applicazioni in cui viene eseguita l'applicazione|
    |*PathToCollectionPlan*|Il percorso di un piano di raccolta, un file XML che configura le impostazioni per l'agente di raccolta.<br /><br /> È possibile specificare un piano fornito insieme all'agente di raccolta. I seguenti piani si applicano alle app Web e alle applicazioni:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Raccoglie solo gli eventi IntelliTrace e SharePoint, incluse le eccezioni, le chiamate al database e le richieste del server Web.<br />-   collection_plan.ASP.NET.trace.xml<br />     Raccoglie le chiamate di funzione e tutti i dati in collection_plan.ASP.NET.default.xml. Questo piano è utile per un'analisi dettagliata, ma può causare un rallentamento dell'app maggiore rispetto a collection_plan.ASP.NET.default.xml.<br /><br /> Per evitare il rallentamento dell'app, personalizzare i piani o creare proprio piano. Per garantire la sicurezza, inserire i piani personalizzati nello stesso percorso sicuro in cui si trovano i file dell'agente di raccolta. Vedere [Creazione e personalizzazione dei piani di raccolta IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) e [Come è possibile ottenere il maggior numero possibile di dati senza rallentare l'applicazione?](#Minimizing) **Nota:**  Per impostazione predefinita, le dimensioni massime del file con estensione iTrace sono pari a 100 MB. Quando il file .iTrace raggiunge il limite, l'agente di raccolta elimina le voci meno recenti del file per liberare spazio per le nuove voci. Per modificare questo limite, modificare l'attributo `MaximumLogFileSize` del piano di raccolta. <br /><br /> *Dove si possono trovare le versioni localizzate di questi piani di raccolta?*<br /><br /> I piani localizzati sono disponibili nelle sottocartelle dell'agente di raccolta.|
    |*FullPathToITraceFileDirectory*|Il percorso completo alla directory di file .iTrace. **Nota sulla sicurezza:**  Specificare il percorso completo, non un percorso relativo.|

     L'agente di raccolta si collega al pool di applicazioni e avvia la raccolta dei dati.

     *È possibile aprire il file .iTrace in questo momento?* No, il file è bloccato durante la raccolta dei dati.

2. Riproduci il problema.

3. Per creare un checkpoint del file con estensione iTrace, usare la sintassi seguente:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Per controllare lo stato della raccolta, usare questa sintassi:

     `Get-IntelliTraceCollectionStatus`

5. Per arrestare la raccolta dei dati, usare questa sintassi:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Dopo aver eseguito il comando, digitare **Y** per confermare che si vuole arrestare la raccolta dei dati. In caso contrario, l'agente di raccolta potrebbe continuare la raccolta dei dati, il file iTrace resta bloccato o il file potrebbe non contenere dati utili.

6. [Aprire il file .iTrace in Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> Raccogliere dati da un'app gestita

1. Per avviare l'app e raccogliere i dati allo stesso tempo, usare questa sintassi:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Ad esempio, per raccogliere i dati da un'app denominata **MyApp**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Nome|Descrizione|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Il percorso completo al file eseguibile dell'agente di raccolta, IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Il percorso di un piano di raccolta, un file XML che configura le impostazioni per l'agente di raccolta.<br /><br /> È possibile specificare un piano fornito insieme all'agente di raccolta. I seguenti piani si applicano alle app gestite:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Raccoglie solo gli eventi IntelliTrace, incluse le eccezioni, le chiamate al database e le richieste del server Web.<br />-   collection_plan.ASP.NET.trace.xml<br />     Raccoglie le chiamate di funzione e tutti i dati in collection_plan.ASP.NET.default.xml. Questo piano è utile per un'analisi dettagliata, ma può causare un rallentamento dell'app maggiore rispetto a collection_plan.ASP.NET.default.xml.<br /><br /> Per evitare il rallentamento dell'app, personalizzare i piani o creare proprio piano. Per garantire la sicurezza, inserire i piani personalizzati nello stesso percorso sicuro in cui si trovano i file dell'agente di raccolta. Vedere [Creazione e personalizzazione dei piani di raccolta IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) e [Come è possibile ottenere il maggior numero possibile di dati senza rallentare l'applicazione?](#Minimizing) **Nota:**  Per impostazione predefinita, le dimensioni massime del file con estensione iTrace sono pari a 100 MB. Quando il file .iTrace raggiunge il limite, l'agente di raccolta elimina le voci meno recenti del file per liberare spazio per le nuove voci. Per modificare questo limite, modificare l'attributo `MaximumLogFileSize` del piano di raccolta. <br /><br /> *Dove si possono trovare le versioni localizzate di questi piani di raccolta?*<br /><br /> I piani localizzati sono disponibili nelle sottocartelle dell'agente di raccolta.|
    |*FullPathToITraceFileDirectoryAndFileName*|Il percorso completo alla directory di file .iTrace e il nome del file .iTrace con estensione **.itrace** . **Nota sulla sicurezza:**  Specificare il percorso completo, non un percorso relativo.|
    |*PathToAppExecutableFileAndFileName*|Il percorso e il nome file dell'app gestita|

2. Arrestare la raccolta dei dati uscendo dall'app.

3. [Aprire il file .iTrace in Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a>Aprire il file con estensione iTrace in Visual Studio Enterprise

> [!NOTE]
> Per eseguire il debug con IntelliTrace ed eseguire il codice seguendo un'istruzione alla volta sono necessari i file di origine corrispondenti e i file di simboli. Vedere [Diagnosticare i problemi dopo la distribuzione.](../debugger/diagnose-problems-after-deployment.md)

1. Spostare il file .iTrace o copiarlo in un computer con Visual Studio Enterprise (ma non edizioni Professional o Community).

2. Fare doppio clic sul file .iTrace all'esterno di Visual Studio oppure aprire il file da Visual Studio.

     Visual Studio visualizza la pagina **Riepilogo di IntelliTrace** . Nella maggior parte delle sezioni è possibile esaminare gli eventi o altri elementi, scegliere un elemento e avviare il debug con IntelliTrace nel punto e nell'ora in cui si è verificato l'evento. Vedere [Uso dei dati IntelliTrace salvati.](../debugger/using-saved-intellitrace-data.md)

    > [!NOTE]
    > Per eseguire il debug con IntelliTrace ed eseguire il codice seguendo un'istruzione alla volta sono necessari i file di origine corrispondenti e i file di simboli nel computer di sviluppo. Vedere [Diagnosticare i problemi dopo la distribuzione.](../debugger/diagnose-problems-after-deployment.md)

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Ricerca per categorie ottenere la maggior parte dei dati senza rallentare l'app?
 IntelliTrace può raccogliere grandi quantità di dati: l'impatto sulle prestazioni dell'app dipende dai dati raccolti da IntelliTrace e dal tipo di codice analizzato. Vedere [Ottimizzazione della raccolta IntelliTrace nei server di produzione](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/).

 Esistono dei metodi per ottenere la maggior quantità di dati possibile senza rallentare l'app:

- Eseguire l'agente di raccolta solo quando si ritiene ci sia un problema o quando è possibile riprodurre il problema.

   Avviare la raccolta, riprodurre il problema, quindi arrestare la raccolta. Aprire il file .iTrace in Visual Studio Enterprise ed esaminare i dati. Vedere [Aprire il file .iTrace in Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- Per le app Web e le applicazioni SharePoint, l'agente di raccolta registra i dati per ciascuna app che condivide il pool di applicazioni specificato. Questo potrebbe rallentare le app che condividono lo stesso pool di applicazioni, anche se è possibile specificare solo i mobili per una singola app in un piano di raccolta.

   Per impedire che l'agente di raccolta rallenti le altre app, ospitare ciascuna app nel proprio pool di applicazioni.

- Esaminare gli eventi nel piano di raccolta per il quale IntelliTrace raccoglie i dati. Modificare il piano di raccolta per disabilitare gli eventi non rilevanti o interessanti.

   Per disabilitare un evento, impostare l'attributo `enabled` per l'elemento `<DiagnosticEventSpecification>` su `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Se l'attributo `enabled` non esiste, l'evento è abilitato.

   *In che modo queste funzionalità migliorano le prestazioni?*

  - È possibile ridurre il tempo di avvio disabilitando gli eventi non rilevanti per l'app. Ad esempio, disabilitare gli eventi di Windows Workflow nelle app che non lo usano.

  - È possibile migliorare le prestazioni sia di avvio che di esecuzione disabilitando gli eventi del Registro di sistema per le app che accedono al Registro di sistema, ma non mostrano problemi con le impostazioni del Registro di sistema.

- Esaminare i moduli nel piano di raccolta per il quale IntelliTrace raccoglie i dati. Modificare il piano di raccolta per includere solo i moduli desiderati:

  1. Aprire il piano di raccolta. Trovare l'elemento `<ModuleList>`.

  2. In `<ModuleList>`, impostare l'attributo `isExclusionList` su `false`.

  3. Usare l'elemento `<Name>` per specificare i singoli moduli con uno degli elementi seguenti: nome file, valore della stringa per includere tutti i moduli il cui nome contiene la stringa specificata oppure chiave pubblica.

     Ad esempio, per raccogliere i dati solo dal modulo Web principale dell'app Web Fabrikam Fiber, creare un elenco come questo visualizzato di seguito:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>
  ```

   Per raccogliere i dati dai moduli il cui nome include "Fabrikam", creare un elenco come questo visualizzato di seguito:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>
  ```

   Per raccogliere i dati dai moduli specificando i relativi token della chiave pubblica, creare un elenco come questo visualizzato di seguito:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>
  ```

   *In che modo queste funzionalità migliorano le prestazioni?*

   Viene ridotta la quantità di informazioni relativa alla chiamata al metodo e gli altri dati di strumentazione raccolti da IntelliTrace quando l'app viene avviata ed eseguita. Questi dati consentono di:

  - Eseguire il codice seguendo un'istruzione alla volta dopo aver raccolto i dati.

  - Esaminare i valori passati e restituiti dalle chiamate di funzione.

    *Perché non si sceglie di escludere i moduli, invece?*

    Per impostazione predefinita, i piani di raccolta escludono i moduli impostando l'attributo `isExclusionList` su `true`. Tuttavia, anche escludendo i moduli, è possibile che i dati vengano raccolti da moduli che non corrispondono ai criteri dell'elenco e che potrebbero quindi essere poco rilevanti, ad esempio moduli di terze parti o open source.

- *Ci sono dati che IntelliTrace non raccoglie?*

   Sì. Per ridurre l'impatto sulle prestazioni, IntelliTrace limita la raccolta dei dati ai valori dei tipi di dati primitivi passati e restituiti dai metodi e ai valori dei tipi di dati primitivi nei campi degli oggetti di primo livello passati e restituiti dai metodi.

   Ad esempio, si supponga di avere una firma del metodo `AlterEmployee` che accetta un numero intero `id` e un oggetto `Employee``oldemployee`:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   Il tipo `Employee` ha i seguenti attributi: `Id`, `Name`e `HomeAddress`. Esiste una relazione di associazione tra `Employee` e il tipo `Address` .

   ![Relazione tra dipendente e indirizzo](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   L'agente di raccolta registra i valori per `id`, `Employee.Id`, `Employee.Name` e l'oggetto `Employee` restituito dal metodo `AlterEmployee` . Tuttavia, l'agente di raccolta non registra le informazioni sull'oggetto `Address` , tranne quelle relative allo stato null o non null. L'agente di raccolta non registra neanche i dati relativi alle variabili locali nel metodo `AlterEmployee` a meno che altri metodi non usino tali variabili come parametri; in questo caso, vengono registrate come parametri del metodo.

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> In quali altri casi è possibile ottenere dati IntelliTrace?

È possibile ottenere dati IntelliTrace da una sessione di debug di IntelliTrace in Visual Studio Enterprise. Vedere [Funzionalità intelliTrace](../debugger/intellitrace-features.md).

## <a name="where-can-i-get-more-information"></a>Dove è possibile ottenere ulteriori informazioni?
 [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blog
 [Uso dell'agente di raccolta autonomo IntelliTrace in remoto](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [Creazione e personalizzazione dei piani di raccolta IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Ottimizzazione della raccolta IntelliTrace nei server di produzione](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forum
 [Debugger di Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Video
 [Video su Channel 9: Raccolta e analisi dei dati IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
