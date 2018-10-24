---
title: Installare Visual Studio 2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: df09e647908b264ade467b8fafd4487641d3be6c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841104"
---
# <a name="install-visual-studio-2015"></a>Installare Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione di installazione più recente di Visual Studio 2017, vedere [installare Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio). Per visualizzare informazioni sull'installazione di versioni precedenti di Visual Studio, fare clic sul collegamento "Altre versioni" nella parte superiore della pagina.

Questa pagina include informazioni dettagliate per l'installazione di **Visual Studio 2015**, la famiglia integrata di strumenti di produttività per sviluppatori. Sono stati inclusi anche alcuni collegamenti che permettono di accedere rapidamente a informazioni su [funzionalità](https://www.visualstudio.com/news/vs2015-vs.aspx), [edizioni](http://go.microsoft.com/fwlink/?LinkID=242142), [requisiti di sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [download](http://go.microsoft.com/fwlink/?LinkId=517106)e altro ancora.  
  

## <a name="quick-links"></a>Collegamenti rapidi  
 Prima di entrare nei dettagli, ecco un elenco dei collegamenti richiesti più frequentemente.  
  
|||  
|------------------|----------------| 
|![Scarica Visual Studio](../install/media/downloads.png "download") |**Scarica**: per installare Visual Studio 2015, è possibile scaricare un file eseguibile prodotto dal [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) pagina (sottoscrizione necessaria) oppure usare il supporto di installazione del prodotto sottoposto a conversione boxing. [Altre informazioni su come scaricare versioni precedente o corrente di Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Altre informazioni sulle funzionalità](../install/media/features.png "funzionalità") |**Le funzionalità**: per altre informazioni sulle funzionalità di Visual Studio 2015, vedere le note sulla versione [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), e [ L'aggiornamento 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|  
|![Scopri le novità in ogni SKU](../install/media/sku.png "SKU") |**Gli SKU**: per scoprire ciò che è disponibile in ogni edizione di Visual Studio 2015, vedere la [confrontare le soluzioni di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142) pagina.|  
|![Visualizzare i requisiti di sistema](../install/media/system-requirements.png "requisiti di sistema") |**Requisiti di sistema**: per visualizzare i requisiti di sistema per ogni edizione di Visual Studio 2015, vedere la [compatibilità di Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) pagina.|  
|![Individuare il codice Product Key](../install/media/product-keys.png "codici Product Key") |**Codici Product Key**: per trovare il codice product key, vedere la [procedura: individuare il codice Product Key di Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) argomento.|  
|![Scopri informazioni sulle licenze](../install/media/licensing.png "contratti multilicenza") |**Gestione delle licenze**: per sapere sulle opzioni di licenza per i singoli utenti o i clienti aziendali, vedere la [licenze Visual Studio e MSDN](https://www.microsoft.com/download/details.aspx?id=13350) white paper.|  
  
##  <a name="custom"></a> Proprietà predefinite installazione personalizzata  
 Quando si installa Visual Studio 2015, è possibile includere o escludere i componenti che verranno usati ogni giorno. Questo vuol dire che un'installazione predefinita sarà spesso di dimensioni inferiori e verrà eseguita più rapidamente rispetto a un'installazione personalizzata. Significa anche che molti componenti che venivano installati per impostazione predefinita nelle versioni precedenti, ora sono considerati componenti personalizzati che è necessario selezionare in modo esplicito in questa versione.  
  
 ![Dialogo di installazione di Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")  
  
 I componenti personalizzati includono Visual C++, Visual F#, SQL Server Data Tools, strumenti mobili multipiattaforma e SDK, oltre a SDK ed estensioni di terze parti. Se i componenti personalizzati non vengono selezionati durante l'installazione iniziale, è possibile installarli in un secondo momento.  
  
> [!NOTE]
>  Un'installazione personalizzata include anche i componenti disponibili con l'installazione predefinita.  
  
 Di seguito è riportato l'elenco completo dei componenti personalizzati:  
  
|Set di funzionalità|Componenti|  
|------------------|----------------|  
|**Aggiornamenti**|Visual Studio 2015 Update 3|  
|**Linguaggi di programmazione**|Visual C++<br />Visual F#<br />Python Tools per Visual Studio|  
|**Windows e sviluppo Web**|Strumenti di pubblicazione ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />PowerShell Tools per Visual Studio (3rd Party)<br />Kit di sviluppo di Silverlight<br />Strumenti per lo sviluppo di app universali di Windows<br />SDK e strumenti di Windows 10<br />Strumenti di Windows 8.1 e Windows Phone 8.0/8.1<br />SDK e strumenti di Windows 8.1|  
|**Sviluppo Mobile multipiattaforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Visual C++ Mobile Development per iOS/Android<br />Clang con Microsoft CodeGen|  
|**Software Development Kit e strumenti comuni**|Android Native Development Kit (3rd Party)<br /> Android SDK [3rd Party]<br />Le API di installazione di Android SDK (3rd Party)<br />Apache Ant (3rd Party)<br /> Java SE Development Kit (3rd Party)<br /> Joyent Node. js (3rd Party)|  
|**Strumenti comuni**|GIT per Windows (3rd Party)<br />Estensione GitHub per Visual Studio (3rd Party)<br /> Strumenti di estendibilità in Visual Studio|  
  
##  <a name="installing"></a> Installazione di Visual Studio  
 È possibile installare Visual Studio usando i supporti di installazione (DVD), usando il servizio di sottoscrizione di Visual Studio dal [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) sito Web, scaricando un programma di installazione web di [Visual Studio Scarica](http://go.microsoft.com/fwlink/?LinkId=517106) sito Web, oppure creare un layout di installazione offline (vedere la [creare una linea installazione di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) pagina per altri dettagli).  
  
> [!IMPORTANT]
>  Per installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]è necessario disporre delle credenziali di amministratore. Tuttavia, dopo l'installazione le credenziali non sono necessarie per usare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Per l'account dell'amministratore locale deve essere abilitati i privilegi seguenti per installare tutti gli elementi in Visual Studio.  
  
|Nome visualizzato dell'oggetto criterio locale|Diritto utente|  
|--------------------------------------|----------------|  
|Backup di file e directory|SeBackupPrivilege|  
|Debug di programmi|SeDebugPrivilege|  
|Gestione registro di controllo e di protezione|SeSecurityPrivilege|  
  
 Per altre informazioni sui requisiti di questo account amministratore locale, vedere l'articolo della Knowledge Base, [L'installazione di SQL Server non riesce se l'account di configurazione non ha determinati diritti utente](https://support.microsoft.com/en-us/kb/2000257).  
  
###  <a name="BKMK_Media"></a> Usando i supporti di installazione  
 Per installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nella directory radice sui supporti di installazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , eseguire il file di installazione per l'edizione preferita:  
  
|Edizione|File di installazione|  
|-------------|-----------------------|  
|Visual Studio Enterprise|vs_enterprise.exe|  
|Visual Studio Professional|vs_professional.exe|  
|Community di Visual Studio|vs_community.exe|  
  
###  <a name="BKMK_Website"></a> Il download dal sito Web del prodotto  
 Visitare il [download di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) pagina e selezionare l'edizione di Visual Studio che si desidera.  
  
### <a name="downloading-from-your-subscription-service"></a>Download dal servizio di sottoscrizione  
 Visitare il [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) pagina e selezionare l'edizione di Visual Studio che si desidera.  
  
###  <a name="BKMK_Offline"></a> Creazione di un layout di installazione offline  
 Se non è il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supporti di installazione, oppure si dispone di una sottoscrizione di Visual Studio, o non si desidera installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando il programma di installazione web, è possibile eseguire un'installazione "disconnected" creando ciò che è noto come offline layout di installazione. Per altre informazioni, vedere la [creare un'installazione Offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) pagina.  
  
##  <a name="enterprise"></a> Distribuzione di Visual Studio in un'organizzazione  
 Per informazioni su come distribuire [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in una rete, vedere la [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).  
  
###  <a name="BKMK_Virtualized"></a> Installazione di Visual Studio in un ambiente virtualizzato  
 **Problemi video con Hyper-V**  
  
 Se si esegue Windows Server 2008 R2 con Hyper-v abilitato e una scheda grafica con accelerazione, è possibile che si verifichino rallentamenti del sistema.  
  
 Per altre informazioni, vedere la seguente pagina sul sito Web Microsoft: [Possibile riduzione delle prestazioni video quando in un computer con Windows Server 2008 o Windows Server 2008 R2 è abilitato il ruolo Hyper-V ed è installata una scheda video con accelerazione](http://go.microsoft.com/fwlink/?LinkID=231084).  
  
 **Emulazione di dispositivi con Hyper-V**  
  
 Quando si installa Visual Studio 2015 sull'hardware effettivo senza virtualizzazione, è possibile scegliere le funzionalità che consentono l'emulazione di dispositivi Windows e Android usando Hyper-V. Quando si esegue l'installazione in Hyper-V, non sarà possibile emulare i dispositivi Windows o Android. Infatti, gli emulatori sono a loro volta macchine virtuali e attualmente non è possibile ospitare una macchina virtuale all'interno di un'altra macchina virtuale. La soluzione alternativa è costituita dagli effettivi dispositivi Windows o Android in cui è possibile distribuire direttamente l'applicazione ed eseguirne il debug.  
  
##  <a name="optionalComponents"></a> Installazione dei componenti facoltativi  
 Se si desidera installare i componenti che potrebbe non essere stata selezionata durante l'installazione originale, usare la procedura seguente.  
  
#### <a name="to-install-optional-components"></a>Per installare i componenti facoltativi  
  
1.  Nella pagina **Programmi e funzionalità**del **Pannello di controllo** selezionare l'edizione del prodotto a cui si vuole aggiungere uno o più componenti, quindi selezionare **Cambia**.  
  
2.  Nell'Installazione guidata scegliere **Modifica**, quindi selezionare i componenti da installare.  
  
3.  Scegliere **Avanti**, quindi seguire le istruzioni rimanenti.  
  
##  <a name="helpContent"></a> Installazione del contenuto della Guida offline  
 Dopo aver installato [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile scaricare ulteriori contenuti della Guida in modo che siano disponibili offline.  
  
#### <a name="to-install-or-uninstall-help-content"></a>Per installare o disinstallare il contenuto della Guida  
  
1. Nella barra dei menu di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , scegliere **?** quindi **Aggiungi e rimuovi contenuto della Guida**.  
  
2. Nella scheda **Gestisci contenuti** di **Microsoft Help Viewer**selezionare l'origine di installazione per il contenuto della Guida.  
  
3. Se sta cercando una raccolta della Guida specifica, immettere il nome o una parola chiave nel **ricerca** casella di testo e quindi premere **invio**.  
  
4. Accanto al nome della raccolta della Guida desiderata, scegliere il collegamento **Aggiungi** o **Rimuovi** .  
  
5. Scegliere il **Update** pulsante.  
  
   Per altre informazioni su come installare o distribuire della Guida offline, vedere la [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md).  
  
##  <a name="serviceReleases"></a> Controllo di Service Release e aggiornamenti del prodotto  
 Poiché non tutte le estensioni sono compatibili, Visual Studio non aggiorna automaticamente le estensioni quando esegue l'aggiornamento da versioni precedenti. È necessario reinstallare le estensioni dal [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.  
  
#### <a name="to-automatically-check-for-service-releases"></a>Per cercare automaticamente versioni di servizio  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Ambiente**, quindi selezionare **Estensioni e aggiornamenti**. Assicurarsi che l'opzione **Controlla automaticamente la disponibilità di aggiornamenti** sia selezionata, quindi scegliere **OK**.  
  
## <a name="registering-visual-studio"></a>Registrazione di Visual Studio  
  
1.  Nella barra dei menu scegliere **Guida**, **Informazioni su**.  
  
     Nella finestra di dialogo **Informazioni su** è indicato il numero di identificazione del prodotto. Per registrare il prodotto sono necessarie le credenziali di account PID e Windows (ad esempio un indirizzo di posta elettronica Hotmail o Outlook.com e una password).  
  
2.  Nella barra dei menu scegliere **Guida**, **Registra prodotto**.  
  
##  <a name="repair"></a> Ripristino di Visual Studio  
  
#### <a name="to-repair-visual-studio"></a>Per ripristinare Visual Studio  
  
1.  Nella pagina **Programmi e funzionalità**del **Pannello di controllo** selezionare l'edizione del prodotto che si vuole ripristinare e fare clic su **Cambia**.  
  
2.  Nell'Installazione guidata scegliere **Ripristina**, scegliere **Avanti**, quindi seguire le istruzioni rimanenti.  
  
#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Per ripristinare Visual Studio in modalità invisibile all'utente o passiva (vale a dire, per ripristinare dall'origine)  
  
1.  Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.  
  
2.  Immettere i seguenti parametri:  
  
     *DVDRoot* \\< File di installazione\> \<lightweightserver /quiet&#124;o passiva > [/norestart] /Repair  
  
##  <a name="troubleshooting"></a> Risoluzione dei problemi di un'installazione  
 Usare queste risorse per ottenere assistenza riguardo problemi di configurazione e installazione:  
  
-   Forum relativo alla[configurazione e installazione di Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190) . Leggere domande e risposte di altri utenti della community di Visual Studio. Se non si trova la risposta desiderata, è possibile porre una domanda.  
  
-   Sito Web del[Supporto tecnico Microsoft per Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019) . Leggere gli articoli della Knowledge Base (KB) e scoprire come contattare il supporto Microsoft per ottenere informazioni sui problemi di installazione di Visual Studio.  
  
-   Per le versioni di Visual Studio 2015, è possibile segnalare un problema tramite il sito Connect all'indirizzo [ https://connect.microsoft.com/visualstudio ](https://connect.microsoft.com/visualstudio).  
  
     È consigliabile includere i log di installazione nella descrizione del problema. È possibile preparare i log per la segnalazione del problema usando Microsoft Visual Studio e lo strumento di raccolta dei log di .NET Framework, come descritto nei passaggi seguenti.  
  
    1.  Scaricare lo strumento di installazione diagnostici da [ http://aka.ms/vscollect ](http://aka.ms/vscollect).  
  
    2.  Eseguire il programma collect.exe da un prompt dei comandi con privilegi elevati.  
  
    3.  Dopo il completamento del programma collect.exe, recuperare il file vslogs.cab dalla directory Temp e caricarlo nel report dei problemi.  
  
##  <a name="relatedTopics"></a> Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Viene descritto come installare Visual Studio quando non si è connessi a Internet.
|[Installare versioni affiancate di Visual Studio](../install/install-visual-studio-versions-side-by-side.md)|Vengono fornite informazioni sull'installazione di più versioni di Visual Studio nello stesso computer.|  
|[Usare i parametri della riga di comando per installare Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Elenca i parametri della riga di comando che è possibile usare quando si installa Visual Studio da un prompt dei comandi.|  
|[Disinstallare Visual Studio](../install/uninstall-visual-studio.md)|Viene descritto come disinstallare Visual Studio.|  
|[Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)|Fornisce informazioni sulle opzioni di distribuzione per Visual Studio.|  
|[The Visual Studio Image Library](../designers/the-visual-studio-image-library.md) (Libreria di immagini di Visual Studio)|Vengono fornite informazioni sull'installazione di immagini che possono essere usate nelle applicazioni di Visual Studio.|  
|[Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Include informazioni e collegamenti che possono aiutarti a usare Visual Studio in modo più efficace.|  
  
## <a name="see-also"></a>Vedere anche  
 [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md) (Accesso a Visual Studio)