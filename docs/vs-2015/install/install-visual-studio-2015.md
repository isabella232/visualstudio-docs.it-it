---
title: Installare Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d593625985924d8c8076e1bdd361ce4d08c1dfbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548044"
---
# <a name="install-visual-studio-2015"></a>Installare Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa pagina include informazioni dettagliate per l'installazione di **Visual Studio 2015**, la famiglia integrata di strumenti di produttività per gli sviluppatori. Sono stati anche inclusi collegamenti per ottenere rapidamente informazioni su [funzionalità](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history), requisiti di [sistema](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs), [download](https://visualstudio.microsoft.com/vs/older-downloads/)e altro ancora.

## <a name="quick-links"></a>Collegamenti rapidi

Prima di entrare nei dettagli, ecco un elenco dei collegamenti richiesti più frequentemente.

|Titolo|Descrizione|
|------------------|----------------|
|![Download di Visual Studio](../install/media/downloads.png "Download") |**Download**: per installare Visual Studio 2015, è possibile scaricare un file eseguibile del prodotto dalla pagina  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (sottoscrizione necessaria) o usare il supporto di installazione dal prodotto boxed. [Altre informazioni su come scaricare le versioni correnti o precedenti di Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Altre informazioni sulle funzionalità](../install/media/features.png "Funzionalità") |**Funzionalità**: per ulteriori informazioni sulle funzionalità di Visual Studio 2015, vedere le note sulla versione per [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)e [Update 3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Visualizzare i requisiti di sistema](../install/media/system-requirements.png "Requisiti di sistema") |**Requisiti di sistema**: per visualizzare i requisiti di sistema per ogni edizione di visual studio 2015, vedere la pagina relativa alla [destinazione e compatibilità della piattaforma Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Individuare il codice Product Key](../install/media/product-keys.png "Codici Product Key") |**Codici Product**Key: per trovare il codice Product Key, vedere l'argomento [procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Scopri le licenze](../install/media/licensing.png "Licenza") |**Gestione**delle licenze: per informazioni sulle opzioni di licenza per singoli utenti o clienti aziendali, vedere il [white paper sulle licenze di Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a> Impostazione predefinita rispetto a installazione personalizzata
 Quando si installa Visual Studio 2015, è possibile includere o escludere i componenti che verranno usati ogni giorno. Questo vuol dire che un'installazione predefinita sarà spesso di dimensioni inferiori e verrà eseguita più rapidamente rispetto a un'installazione personalizzata. Significa anche che molti componenti che venivano installati per impostazione predefinita nelle versioni precedenti, ora sono considerati componenti personalizzati che è necessario selezionare in modo esplicito in questa versione.

 ![Finestra di dialogo di installazione di Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 I componenti personalizzati includono Visual C++, Visual F#, SQL Server Data Tools, gli SDK e gli strumenti per dispositivi mobili multipiattaforma e gli SDK e le estensioni di terze parti. Se i componenti personalizzati non vengono selezionati durante l'installazione iniziale, è possibile installarli in un secondo momento.

> [!NOTE]
> Un'installazione personalizzata include anche i componenti disponibili con l'installazione predefinita.

 Di seguito è riportato l'elenco completo dei componenti personalizzati:

|Set di funzionalità|Componenti|
|------------------|----------------|
|**Aggiornamenti**|Visual Studio 2015 Update 3|
|**Linguaggi di programmazione**|Visual C++<br />Visual F#<br />Python Tools per Visual Studio|
|**Windows e sviluppo Web**|Strumenti di pubblicazione ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (terze parti)<br />Kit di sviluppo di Silverlight<br />Strumenti per lo sviluppo di app universali di Windows<br />SDK e strumenti di Windows 10<br />Strumenti di Windows 8.1 e Windows Phone 8.0/8.1<br />SDK e strumenti di Windows 8.1|
|**Sviluppo multipiattaforma per dispositivi mobili**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ Mobile Development per iOS/Android<br />Clang con Microsoft CodeGen|
|**Strumenti comuni e Software Development Kit**|Android Native Development Kit (terze parti)<br /> Android SDK [terze parti]<br />API di installazione di Android SDK (terze parti)<br />Apache Ant (terze parti)<br /> Java SE Development Kit (terze parti)<br /> Node.js Joyent (terze parti)|
|**Strumenti comuni**|Git per Windows (terze parti)<br />Estensione GitHub per Visual Studio (terze parti)<br /> Strumenti di estendibilità in Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a> Installare Visual Studio
 È possibile installare Visual Studio usando i supporti di installazione (DVD), usando il servizio di sottoscrizione di Visual Studio dal sito Web [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , scaricando un programma di installazione Web dal sito Web di [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) oppure creando un layout di installazione offline. per altre informazioni, vedere la pagina [creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

> [!IMPORTANT]
> Per installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]è necessario disporre delle credenziali di amministratore. Tuttavia, dopo l'installazione le credenziali non sono necessarie per usare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Per l'account dell'amministratore locale deve essere abilitati i privilegi seguenti per installare tutti gli elementi in Visual Studio.

|Nome visualizzato dell'oggetto criterio locale|Diritto utente|
|--------------------------------------|----------------|
|Backup di file e directory|SeBackupPrivilege|
|Debug di programmi|SeDebugPrivilege|
|Gestione registro di controllo e di protezione|SeSecurityPrivilege|

 Per altre informazioni sui requisiti di questo account amministratore locale, vedere l'articolo della Knowledge Base, [L'installazione di SQL Server non riesce se l'account di configurazione non ha determinati diritti utente](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a> USA supporto di installazione
 Per installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nella directory radice sui supporti di installazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , eseguire il file di installazione per l'edizione preferita:

|Edizione|File di installazione|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Community di Visual Studio|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a> Download dal sito Web del prodotto
 Visitare la pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) e selezionare l'edizione di Visual Studio desiderata.

### <a name="download-from-your-subscription-service"></a>Scarica dal servizio di sottoscrizione
 Visitare la pagina [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) e selezionare l'edizione di Visual Studio desiderata.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a> Creare un layout di installazione offline
 Se non si dispone del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supporto di installazione di oppure non si dispone di una sottoscrizione di Visual Studio o non si desidera eseguire l'installazione tramite [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] il programma di installazione Web, è possibile eseguire un'installazione "disconnessa" creando un layout noto come layout di installazione offline. Per ulteriori informazioni, vedere la pagina [creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a> Distribuire Visual Studio in un'organizzazione
 Per informazioni su come eseguire [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la distribuzione in una rete, vedere la [Guida dell'amministratore di Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a> Installare Visual Studio in un ambiente virtualizzato
 **Problemi video con Hyper-V**

 Se si esegue Windows Server 2008 R2 con Hyper-v abilitato e una scheda grafica con accelerazione, è possibile che si verifichino rallentamenti del sistema.

 Per ulteriori informazioni, vedere [riduzione delle prestazioni video quando in un computer con Windows server 2008 o Windows server 2008 R2 è abilitato il ruolo Hyper-V e viene installata una scheda video con accelerazione](https://support.microsoft.com/kb/961661).

 **Emulazione di dispositivi con Hyper-V**

 Quando si installa Visual Studio 2015 sull'hardware effettivo senza virtualizzazione, è possibile scegliere le funzionalità che consentono l'emulazione di dispositivi Windows e Android usando Hyper-V. Quando si esegue l'installazione in Hyper-V, non sarà possibile emulare i dispositivi Windows o Android. Infatti, gli emulatori sono a loro volta macchine virtuali e attualmente non è possibile ospitare una macchina virtuale all'interno di un'altra macchina virtuale. La soluzione alternativa è costituita dagli effettivi dispositivi Windows o Android in cui è possibile distribuire direttamente l'applicazione ed eseguirne il debug.

## <a name="install-optional-components"></a><a name="optionalComponents"></a> Installare i componenti facoltativi
 Se si desidera installare componenti che potrebbero non essere stati selezionati durante l'installazione originale, attenersi alla procedura riportata di seguito.

#### <a name="to-install-optional-components"></a>Per installare i componenti facoltativi

1. Nella pagina **Programmi e funzionalità**del **Pannello di controllo** selezionare l'edizione del prodotto a cui si vuole aggiungere uno o più componenti, quindi selezionare **Cambia**.

2. Nell'Installazione guidata scegliere **Modifica**, quindi selezionare i componenti da installare.

3. Scegliere **Avanti**, quindi seguire le istruzioni rimanenti.

## <a name="install-offline-help-content"></a><a name="helpContent"></a> Installare il contenuto della Guida offline
 Dopo aver installato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile scaricare ulteriori contenuti della Guida in modo che siano disponibili offline.

#### <a name="to-install-or-uninstall-help-content"></a>Per installare o disinstallare il contenuto della Guida

1. Nella barra dei menu di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , scegliere **?** quindi **Aggiungi e rimuovi contenuto della Guida**.

2. Nella scheda **Gestisci contenuti** di **Microsoft Help Viewer**selezionare l'origine di installazione per il contenuto della Guida.

3. Se si cerca una raccolta specifica della Guida, immettere il nome o una parola chiave nella casella di testo **Cerca**, quindi premere **INVIO**.

4. Accanto al nome della raccolta della Guida desiderata, scegliere il collegamento **Aggiungi** o **Rimuovi** .

5. Fare clic sul pulsante **Aggiorna**.

   Per ulteriori informazioni su come installare o distribuire la Guida offline, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a> Verifica della disponibilità di Service Release e degli aggiornamenti del prodotto
 Poiché non tutte le estensioni sono compatibili, Visual Studio non aggiorna automaticamente le estensioni quando si esegue l'aggiornamento da versioni precedenti. È necessario reinstallare le estensioni dal [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o dall'autore del software.

#### <a name="to-automatically-check-for-service-releases"></a>Per cercare automaticamente versioni di servizio

1. Sulla barra dei menu scegliere **strumenti**, **Opzioni**.

2. Nella finestra di dialogo **Opzioni** espandere **Ambiente**, quindi selezionare **Estensioni e aggiornamenti**. Assicurarsi che l'opzione **Controlla automaticamente la disponibilità di aggiornamenti** sia selezionata, quindi scegliere **OK**.

## <a name="register-visual-studio"></a>Registrare Visual Studio

1. Nella barra dei menu scegliere **Guida**, **Informazioni su**.

     Nella finestra di dialogo **Informazioni su** è indicato il numero di identificazione del prodotto. Per registrare il prodotto sono necessarie le credenziali di account PID e Windows (ad esempio un indirizzo di posta elettronica Hotmail o Outlook.com e una password).

2. Nella barra dei menu scegliere **Guida**, **Registra prodotto**.

## <a name="repair-visual-studio"></a><a name="repair"></a> Ripristinare Visual Studio

#### <a name="to-repair-visual-studio"></a>Per ripristinare Visual Studio

1. Nella pagina **Programmi e funzionalità**del **Pannello di controllo** selezionare l'edizione del prodotto che si vuole ripristinare e fare clic su **Cambia**.

2. Nell'Installazione guidata scegliere **Ripristina**, scegliere **Avanti**, quindi seguire le istruzioni rimanenti.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Per ripristinare Visual Studio in modalità invisibile all'utente o passiva (ovvero per ripristinare dall'origine)

1. Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.

2. Immettere i parametri seguenti:

     *DVDRoot* \\ DVDRoot < *File* \> di installazione \<`/quiet|/passive`> [/`norestart`]/`Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a> Risolvere i problemi relativi a un'installazione
 Usare queste risorse per ottenere assistenza riguardo problemi di configurazione e installazione:

- Forum relativo alla[configurazione e installazione di Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads) . Leggere domande e risposte di altri utenti della community di Visual Studio. Se non si trova la risposta desiderata, è possibile porre una domanda.

- [Ottenere assistenza con Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Trovare articoli della Knowledge base (KB) e informazioni su come contattare supporto tecnico Microsoft per informazioni sui problemi relativi all'installazione di Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a> Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Viene descritto come installare Visual Studio quando non si è connessi a Internet.
|[Installare le versioni di Visual Studio side-by-side](../install/install-visual-studio-versions-side-by-side.md)|Vengono fornite informazioni sull'installazione di più versioni di Visual Studio nello stesso computer.|
|[Usare i parametri della riga di comando per installare Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Elenca i parametri della riga di comando che è possibile usare quando si installa Visual Studio da un prompt dei comandi.|
|[Disinstallare Visual Studio](../install/uninstall-visual-studio.md)|Viene descritto come disinstallare Visual Studio.|
|[Guida dell'amministratore di Visual Studio](../install/visual-studio-administrator-guide.md)|Fornisce informazioni sulle opzioni di distribuzione per Visual Studio.|
|[Libreria di immagini di Visual Studio](../designers/the-visual-studio-image-library.md)|Vengono fornite informazioni sull'installazione di immagini che possono essere usate nelle applicazioni di Visual Studio.|
|[Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Include informazioni e collegamenti che consentono di usare Visual Studio in modo più efficace.|

## <a name="see-also"></a>Vedere anche

- [Accesso a Visual Studio](../ide/signing-in-to-visual-studio.md)
