---
title: Risolvere i problemi relativi alla distribuzione di soluzioni OfficeTroubleshoot Office solution deployment
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444934"
---
# <a name="troubleshoot-office-solution-deployment"></a>Risolvere i problemi relativi alla distribuzione di soluzioni OfficeTroubleshoot Office solution deployment
  Questo argomento contiene informazioni su come risolvere i problemi comuni che possono verificarsi durante la distribuzione di soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Risolvere i problemi relativi alle soluzioni Office tramite il Visualizzatore eventi
 È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di errore acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione. Per ulteriori informazioni, vedere [Registrazione eventi per soluzioni Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>La modifica del nome dell'assembly causa conflitti
 Se si modifica il valore **Nome assembly** nella pagina **Applicazione** di **Progettazione progetti** dopo aver già distribuito una soluzione, gli strumenti di pubblicazione modificheranno il pacchetto di installazione in modo che disponga di un file *Setup.exe* e di due manifesti di distribuzione. Se si distribuiscono due file manifesto, potrebbero verificarsi le condizioni seguenti:

- Se l'utente finale installa entrambe le versioni, l'applicazione caricherà entrambi i componenti aggiuntivi VSTO.

- Se il componente aggiuntivo VSTO è stato installato prima della modifica del nome dell'assembly, l'utente finale non riceverà mai aggiornamenti.

  Per evitare queste condizioni, non modificare il valore **di Nome assembly** della soluzione dopo la distribuzione della soluzione.

## <a name="check-for-updates-takes-a-long-time"></a>Verificare la disponibilità di aggiornamenti richiede molto tempo
 Visual Studio 2010 Tools per Office RuntimeVisual Studio 2010 Tools for Office runtime fornisce una voce del Registro di sistema che gli amministratori possono utilizzare per impostare il valore di timeout per il download dei manifesti e della soluzione.

#### <a name="to-set-the-time-out-value"></a>Per impostare il valore di timeout

1. Nel Registro di sistema passare alla chiave seguente:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. Nella sottochiave **AddInTimeout** impostare il valore di timeout in millisecondi.

     Se la sottochiave **AddInTimeout** non esiste, crearla come DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Impossibile aggiornare o pubblicare in una condivisione file di rete
 Le soluzioni Office che si trovano in una condivisione file di rete potrebbero visualizzare un messaggio fuorviante durante gli aggiornamenti se il file *Setup.exe* della soluzione è bloccato in un processo durante la pubblicazione dell'aggiornamento. Il messaggio può essere analogo al seguente: "Impossibile aggiungere 'setup.exe' al sito Web. Il file 'setup.exe' esiste già nel sito Web".

 Per evitare il blocco del file, si può impostare la condivisione come di sola lettura per gli utenti finali. Se però nella condivisione sono presenti documenti, anche questi diventeranno di sola lettura per gli utenti finali.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Prerequisiti per Microsoft Office non installati
 È possibile aggiungere .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]e gli assembly di interoperabilità primari di Microsoft Office al pacchetto di installazione come prerequisiti distribuiti con la soluzione Office. Per informazioni su come installare gli assembly di interoperabilità primari, vedere [Configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) e [Procedura: installare assembly](../vsto/how-to-install-office-primary-interop-assemblies.md)di interoperabilità primari di Office .

## <a name="publish-using-localhost-can-cause-installation-problems"></a>La pubblicazione tramite Localhost può causare problemi di installazione
 Quando si `http://localhost` utilizza come percorso di pubblicazione o installazione per le soluzioni a livello di documento, la **Pubblicazione guidata** non converte la stringa nel nome reale del computer. In questo caso, è necessario installare la soluzione nel computer di sviluppo. Per fare in modo che le soluzioni distribuite usino IIS nel computer di sviluppo, usare il nome completo per tutti i percorsi HTTP/HTTPS/FTP anziché localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Gli assembly memorizzati nella cache vengono caricati anziché gli assembly aggiornati
 Fusion, il caricatore di assembly di .NET Framework, carica la copia degli assembly memorizzata nella cache quando il percorso di output del progetto è in una condivisione file di rete, l'assembly è firmato con un nome sicuro e la versione dell'assembly della personalizzazione non cambia. Se si aggiorna un assembly che soddisfa queste condizioni, l'aggiornamento non verrà visualizzato la volta successiva che si esegue il progetto perché viene caricata la copia memorizzata nella cache.

 È possibile configurare Visual Studio in modo che Fusion scarichi gli assembly ogni volta che si esegue il progetto.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Per scaricare gli assembly anziché caricare le copie memorizzate nella cache

1. Sulla barra dei menu scegliere **Progetto**, _Proprietà_**NomeProgetto**.

2. Nella pagina **Applicazione** scegliere **Informazioni assembly**.

3. Impostare il numero di revisione, il terzo campo,\*della **versione dell'assieme**, su un carattere jolly ( ). Ad esempio, "1.0."  Quindi scegliere il pulsante **OK.**

   Dopo aver modificato la versione dell'assembly, è possibile continuare a firmare l'assembly con nome sicuro e Fusion caricherà la versione più recente della personalizzazione.

 [!NOTE]
> A partire da Visual Studio 2017, se si tenta di utilizzare caratteri jolly nella versione assembly si verificherà un errore di compilazione.  Ciò è dovuto al fatto che i caratteri jolly nella versione dell'assembly interromperanno la funzionalità deterministica di MSBuild. Verrà richiesto di rimuovere i caratteri jolly dalla versione dell'assembly o di disabilitare il determinismo.  Per altre informazioni sulla funzionalità deterministica, vedere: Proprietà comuni del progetto MSBuild e [Personalizzare la compilazioneTo](../msbuild/customize-your-build.md) learn more about the Deterministic feature see: [Common MSBuild project properties](../msbuild/common-msbuild-project-properties.md) and Customize your build

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>L'installazione non riesce quando l'URI contiene caratteri che non sono US-ASCII
 Quando si pubblica una soluzione Office in un percorso HTTP/HTTPS/FTP, il percorso non può contenere caratteri Unicode non US-ASCII. Questi caratteri possono causare un comportamento incoerente nel programma di installazione. Usare caratteri US-ASCII per il percorso di installazione.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Richiesta di disinstallazione manuale viene visualizzato quando si pubblica e si installa una soluzione nel computer di sviluppo
 Quando si compila una soluzione Office, la versione compilata viene registrata automaticamente. Se la stessa soluzione è stata precedentemente pubblicata e installata nel computer di sviluppo, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rileva che i percorsi di installazione per la versione pubblicata e la versione compilata sono diversi dopo la successiva compilazione, ricompilazione o pubblicazione della soluzione. Il messaggio di errore è: "Impossibile installare la personalizzazione perché ne è installata un'altra versione che non può essere aggiornata da questo percorso". Le chiavi del Registro di sistema vengono aggiornate ogni volta che una soluzione viene ricompilata. Pertanto, prima della pubblicazione, del debug o dell'esecuzione della nuova versione, occorre disinstallare la versione precedente.

 Per evitare la comparsa del messaggio, creare un altro account utente nel computer di sviluppo per testare la distribuzione. In alternativa, si può disinstallare la versione dall'elenco dei programmi installati nel computer prima di procedere alla pubblicazione, al debug o alla ricompilazione della soluzione.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Eccezione non rilevata o errore di metodo non trovato quando si installa una soluzioneUncaught exception or method not found error when you install a solution
 Quando si installano soluzioni Office aprendo il manifesto di distribuzione (un file *vsto),* un'applicazione di Office, un documento o una cartella di lavoro, potrebbero essere visualizzati messaggi di errore per le condizioni seguenti:

- Impossibile trovare il metodo.

- MissingMethodException.

- Eccezione non rilevata.

  Per evitare questi messaggi di errore, installare la soluzione eseguendo il programma di installazione.

  Quando si installa la soluzione senza eseguire il programma di installazione, non vengono cercati o installati i prerequisiti. Il programma di installazione verifica la versione corretta dei prerequisiti e li installa, se necessario.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Le chiavi del Registro di sistema del manifesto per i componenti aggiuntivi cambiano dopo la compilazione di un progetto InstallShield Limited EditionManifest registry keys for Add-ins change after an InstallShield Limited Edition project is built
 La chiave del Registro di sistema del manifesto che fa parte di un programma di installazione del componente aggiuntivo VSTO a volte cambia da *vsto* a *.dll.manifest* quando si compila un progetto InstallShield Limited Edition.

 Per risolvere questo problema, creare il progetto InstallShield Limited Edition in una soluzione diversa oppure usare CompanyName.AddinName come valore della chiave del Registro di sistema che contiene il nome del componente aggiuntivo VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Il programma di installazione ClickOnce per la soluzione Office non installa gli assembly di interoperabilità primari
 Quando si esegue il programma di installazione creato da ClickOnce per la soluzione Office, il programma di installazione per gli assembly di interoperabilità primari di Office viene eseguito solo se non sono già installati assembly di interoperabilità primari.

 Se il programma di installazione non installa correttamente gli assembly di interoperabilità utente, installarli manualmente eseguendo il file del programma di installazione denominato *o2007pia.msi* dalla directory di installazione.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>La reinstallazione di soluzioni Office causa un'eccezione non compresa nell'intervallo
 Quando si reinstalla una soluzione Office, è possibile che venga visualizzata un'eccezione <xref:System.ArgumentOutOfRangeException> con il messaggio di errore seguente: Argomento specificato non compreso nell'intervallo.

 Questa situazione si verifica se la combinazione di maiuscole e minuscole per l'URL del percorso di installazione è diversa. Ad esempio, questo errore viene visualizzato se `http://fabrikam.com/ExcelSolution.vsto` è stata installata una soluzione Office dalla prima volta e quindi utilizzato `http://fabrikam.com/excelsolution.vsto` la seconda volta.

 Per evitare che venga visualizzato il messaggio, usare la stessa combinazione di maiuscole e minuscole quando si installano soluzioni Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Impossibile installare una soluzione ClickOnce aprendo il manifesto di distribuzione dal Web
 Gli utenti possono installare soluzioni Office aprendo il manifesto della distribuzione dal Web. Tuttavia, alcune installazioni di Internet Information Services (IIS) bloccano l'estensione di file *vsto.* È necessario definire il tipo MIME in IIS prima di utilizzarlo per distribuire una soluzione Office.

 Per informazioni su come definire il tipo MIME in IIS 7, vedere [Aggiungere un tipo MIME (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Impostare l'estensione **.vsto** e il tipo MIME su **application/x-ms-vsto**.

## <a name="see-also"></a>Vedere anche

- [Risolvere i problemi relativi alle distribuzioni ClickOnceTroubleshoot ClickOnce deployments](../deployment/troubleshooting-clickonce-deployments.md)
- [Distribuire una soluzione OfficeDeploy an Office solution](../vsto/deploying-an-office-solution.md)
