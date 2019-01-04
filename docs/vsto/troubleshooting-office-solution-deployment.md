---
title: Risolvere i problemi di distribuzione di soluzioni Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5d6dc3a871389b8b7624b31a4f2a4d3e4e185865
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947257"
---
# <a name="troubleshoot-office-solution-deployment"></a>Risolvere i problemi di distribuzione di soluzioni Office
  Questo argomento contiene informazioni su come risolvere i problemi comuni che possono verificarsi durante la distribuzione di soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Risolvere i problemi di soluzioni Office usando il Visualizzatore eventi
 È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di errore acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione. Per altre informazioni, vedere [la registrazione degli eventi per le soluzioni Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Modifica il nome dell'assembly causa conflitti
 Se si modifica il **nome dell'Assembly** valore nel **applicazione** pagina del **Progettazione progetti** quando una soluzione già stata distribuita, gli strumenti di pubblicazione modificheranno il Pacchetto di installazione di averne *Setup.exe* file e due manifesti di distribuzione. Se si distribuiscono due file manifesto, potrebbero verificarsi le condizioni seguenti:

- Se l'utente finale installa entrambe le versioni, l'applicazione caricherà entrambi i componenti aggiuntivi VSTO.

- Se il componente aggiuntivo VSTO è stato installato prima della modifica del nome dell'assembly, l'utente finale non riceverà mai aggiornamenti.

  Per evitare queste situazioni, non modificare la soluzione **nome dell'Assembly** valore dopo aver distribuito la soluzione.

## <a name="check-for-updates-takes-a-long-time"></a>Presenza di aggiornamenti richiede molto tempo
 Visual Studio 2010 Tools per Office runtime fornisce una voce del Registro di sistema che gli amministratori possono utilizzare per impostare il valore di timeout per il download dei manifesti e della soluzione.

#### <a name="to-set-the-time-out-value"></a>Per impostare il valore di timeout

1.  Nel Registro di sistema passare alla chiave seguente:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2.  Nella sottochiave **AddInTimeout** impostare il valore di timeout in millisecondi.

     Se la sottochiave **AddInTimeout** non esiste, crearla come DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Non è possibile aggiornare o pubblicare in una condivisione file di rete
 Soluzioni Office che si trovano in una condivisione file di rete potrebbero visualizzare un messaggio fuorviante durante gli aggiornamenti se la soluzione *Setup.exe* file è bloccato in un processo durante l'aggiornamento è in corso di pubblicazione. Il messaggio potrebbe essere il seguente: "Impossibile aggiungere 'setup.exe' sul Web. Il file 'setup.exe' esiste già nel sito Web".

 Per evitare il blocco del file, si può impostare la condivisione come di sola lettura per gli utenti finali. Se però nella condivisione sono presenti documenti, anche questi diventeranno di sola lettura per gli utenti finali.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Non sono installati i prerequisiti per Microsoft Office
 È possibile aggiungere .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]e gli assembly di interoperabilità primari di Microsoft Office al pacchetto di installazione come prerequisiti distribuiti con la soluzione Office. Per informazioni su come installare l'assembly di interoperabilità primari, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) e [come: Installare l'assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>La pubblicazione mediante 'Localhost' può causare problemi di installazione
 Quando si usa "<http://localhost>" come percorso di pubblicazione o di installazione per le soluzioni a livello di documento, il **pubblicazione guidata** non converte la stringa per il nome effettivo del computer. In questo caso, è necessario installare la soluzione nel computer di sviluppo. Per fare in modo che le soluzioni distribuite usino IIS nel computer di sviluppo, usare il nome completo per tutti i percorsi HTTP/HTTPS/FTP anziché localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Gli assembly memorizzati nella cache vengono caricati anziché gli assembly aggiornati
 Fusion, il caricatore di assembly di .NET Framework, carica la copia degli assembly memorizzata nella cache quando il percorso di output del progetto è in una condivisione file di rete, l'assembly è firmato con un nome sicuro e la versione dell'assembly della personalizzazione non cambia. Se si aggiorna un assembly che soddisfa queste condizioni, l'aggiornamento non verrà visualizzato la volta successiva che si esegue il progetto perché viene caricata la copia memorizzata nella cache.

 È possibile configurare Visual Studio in modo che Fusion scarichi gli assembly ogni volta che si esegue il progetto.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Per scaricare gli assembly anziché caricare le copie memorizzate nella cache

1. Sulla barra dei menu scegliere **Progetto**, _Proprietà_**NomeProgetto**.

2. Nella pagina **Applicazione** scegliere **Informazioni assembly**.

3. Nel primo **versione dell'Assembly** immettere un asterisco (\*), quindi scegliere il **OK** pulsante.

   Dopo aver modificato la versione dell'assembly, è possibile continuare a firmare l'assembly con nome sicuro e Fusion caricherà la versione più recente della personalizzazione.

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Installazione non riesce se l'URI contiene caratteri non US-ASCII
 Quando si pubblica una soluzione Office in un percorso HTTP/HTTPS/FTP, il percorso non può contenere caratteri Unicode non US-ASCII. Questi caratteri possono causare un comportamento incoerente nel programma di installazione. Usare caratteri US-ASCII per il percorso di installazione.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Richiesta di disinstallazione manuale viene visualizzata quando si pubblica e si installa una soluzione nel computer di sviluppo
 Quando si compila una soluzione Office, la versione compilata viene registrata automaticamente. Se la stessa soluzione è stata precedentemente pubblicata e installata nel computer di sviluppo, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rileva che i percorsi di installazione per la versione pubblicata e la versione compilata sono diversi dopo la successiva compilazione, ricompilazione o pubblicazione della soluzione. Il messaggio di errore è: "Impossibile installare la personalizzazione perché ne è installata un'altra versione che non può essere aggiornata da questo percorso". Le chiavi del Registro di sistema vengono aggiornate ogni volta che una soluzione viene ricompilata. Pertanto, prima della pubblicazione, del debug o dell'esecuzione della nuova versione, occorre disinstallare la versione precedente.

 Per evitare la comparsa del messaggio, creare un altro account utente nel computer di sviluppo per testare la distribuzione. In alternativa, si può disinstallare la versione dall'elenco dei programmi installati nel computer prima di procedere alla pubblicazione, al debug o alla ricompilazione della soluzione.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Eccezione non rilevata o un metodo non trovato errore quando si installa una soluzione
 Quando si installano soluzioni Office aprendo il manifesto di distribuzione (un *VSTO* file), possono essere visualizzati messaggi di errore di applicazione, un documento o cartella di lavoro, Office per le condizioni seguenti:

- Impossibile trovare il metodo.

- MissingMethodException.

- Eccezione non rilevata.

  Per evitare questi messaggi di errore, installare la soluzione eseguendo il programma di installazione.

  Quando si installa la soluzione senza eseguire il programma di installazione, non vengono cercati o installati i prerequisiti. Il programma di installazione verifica la versione corretta dei prerequisiti e li installa, se necessario.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifesto le chiavi del Registro di sistema per la modifica di componenti aggiuntivi dopo la compilazione di un progetto InstallShield Limited Edition
 La chiave del Registro di sistema del manifesto che fa parte di un'installazione del componente aggiuntivo VSTO talvolta programmare modifiche rispetto *VSTO* al *. manifest* quando si compila un progetto InstallShield Limited Edition.

 Per risolvere questo problema, creare il progetto InstallShield Limited Edition in una soluzione diversa oppure usare CompanyName.AddinName come valore della chiave del Registro di sistema che contiene il nome del componente aggiuntivo VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Il programma di installazione ClickOnce per la soluzione Office non installa gli assembly di interoperabilità primari
 Quando si esegue il programma di installazione creato da ClickOnce per la soluzione Office, il programma di installazione per gli assembly di interoperabilità primari di Office viene eseguito solo se non sono già installati assembly di interoperabilità primari.

 Se il programma di installazione non installa l'assembly di interoperabilità primari correttamente, installarli manualmente eseguendo il file di programma di installazione denominato *o2007pia.msi* dalla directory di installazione.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Reinstallare un argomento non compreso nell'eccezione compreso nell'intervallo cause di soluzioni Office
 Quando si reinstalla una soluzione Office, un <xref:System.ArgumentOutOfRangeException> eccezione potrebbe essere visualizzato con il messaggio di errore seguente: Argomento specificato non compreso nell'intervallo di valori validi.

 Questa situazione si verifica se la combinazione di maiuscole e minuscole per l'URL del percorso di installazione è diversa. Ad esempio, questo errore può essere visualizzato se è stata installata una soluzione Office dal [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) la prima volta e quindi usati [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) la seconda volta.

 Per evitare che venga visualizzato il messaggio, usare la stessa combinazione di maiuscole e minuscole quando si installano soluzioni Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Non è possibile installare una soluzione ClickOnce aprendo il manifesto di distribuzione dal web
 Gli utenti possono installare soluzioni Office aprendo il manifesto della distribuzione dal Web. Tuttavia, di bloccare alcune installazioni di Internet Information Services (IIS) di *VSTO* estensione del nome file. È necessario definire il tipo MIME in IIS prima di usarla per distribuire una soluzione Office.

 Per informazioni su come definire il tipo MIME in IIS 7, vedere [aggiungere un tipo MIME (IIS 7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Impostare l'estensione **.vsto** e il tipo MIME su **application/x-ms-vsto**.

## <a name="see-also"></a>Vedere anche

- [Risolvere i problemi di distribuzioni ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
