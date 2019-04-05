---
title: Risoluzione dei problemi relativi a pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16988915c9e8353cfc26f32e7d83c556c7f4957d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001494"
---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono i problemi comuni che potrebbero aver con il pacchetto VSPackage e suggerimenti per risolvere i problemi.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere i problemi di un pacchetto VSPackage che impedisce l'avvio di Visual Studio  
  
-   Avviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria.  
  
     Per avviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria, un prompt dei comandi, digitare **/safemode devenv.exe**.  
  
     Durante questo processo non VSPackage vengono caricati, ad eccezione di pacchetti VSPackage che sono inclusi con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere i problemi di un pacchetto VSPackage che non viene caricato  
  
1.  Assicurarsi che si sta utilizzando la radice del Registro di sistema in cui il VSPackage è registrato per l'esecuzione, in genere la radice del Registro di sistema sperimentale.  
  
     Per altre informazioni, vedere [il processo dell'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
2.  Se il pacchetto VSPackage è la destinazione per l'esecuzione nella radice del Registro di sistema sperimentale, assicurarsi che si esegue la versione sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Per eseguire la versione sperimentale, digitare quanto segue in una finestra di comando: **devenv /rootsuffix exp**.  
  
3.  Verificare le voci del Registro di sistema di VSPackage.  
  
     Per altre informazioni, vedere [la registrazione di pacchetti VSPackage](internals/registering-vspackages.md) e [gestione dei pacchetti VSPackage](../extensibility/managing-vspackages.md).  
  
4.  Aprire il **Output** finestra dell'istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che non riesce a caricare il pacchetto VSPackage. Informazioni sui motivi per cui il pacchetto VSPackage non riesce a caricare potrebbero essere visualizzate in tale finestra.  
  
    > [!NOTE]
    >  Se si avvia la versione sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dal [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE), esaminare le **Output** finestra di entrambe le versioni.  
  
5.  Esaminare il log attività.  
  
     Per altre informazioni, vedere [Procedura: Usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Per altre informazioni sulle eccezioni generate dall'IDE, fare clic su **eccezioni** nel **Debug** menu per abilitare le eccezioni. Nel **eccezioni** nella finestra di dialogo selezionare i tipi di eccezioni intorno al quale si desiderano altre informazioni.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere i problemi di un pacchetto VSPackage che registra  
  
1.  Assicurarsi che l'assembly VSPackage si trova in una posizione attendibile. RegPkg non è possibile registrare gli assembly in una posizione non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione di sicurezza predefinito .net. Anche se viene visualizzato un avviso ogni volta che un utente crea un progetto in una posizione non attendibile, la casella di controllo "non visualizzare più questo messaggio" può impedire questo avviso non venga ricorrente.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi di un comando che non è visibile o che genera un errore quando si fa clic su un comando  
  
1.  Unire i comandi di menu nuove o modificate e quelli già nell'IDE, digitando quanto segue al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prompt dei comandi: **devenv /rootsuffix Exp /setup**.  
  
2.  Verificare che l'opzione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] reperibile UI.dll per il pacchetto VSPackage.  
  
    1.  Trovare il CLSID del pacchetto VSPackage nella sezione pacchetti del Registro di sistema:  
  
         Studio HKLM\Software\Microsoft\Visual\\*\<versione >* \Packages  
  
    2.  Verificare che il percorso specificato dalla sottochiave SatelliteDll sia corretto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere i problemi di un pacchetto VSPackage che si comporta in modo imprevisto  
  
1.  Impostare i punti di interruzione nel codice.  
  
     I punti di partenza ottimali per il debug sono il costruttore e il metodo di inizializzazione. È anche possibile impostare i punti di interruzione nell'area di cui che si vuole valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire il debugger.  
  
    1.  Scegliere **Proprietà** dal menu **Progetto**.  
  
    2.  Nel **pagine delle proprietà** finestra di dialogo, seleziona la **Debug** scheda.  
  
    3.  Nel **argomenti della riga di comando** , digitare il suffisso di radice dell'ambiente di sviluppo che il pacchetto VSPackage è destinato. Ad esempio, per selezionare la build sperimentale, digitare: **RootSuffix Exp**.  
  
    4.  Nel **Debug** menu, fare clic su **Avvia debug** o premere F5.  
  
        > [!NOTE]
        >  Se si esegue il debug di un progetto, creare o caricare un'istanza esistente del progetto a questo punto.  
  
2.  Usare il log attività.  
  
     Tracciare il comportamento di VSPackage scrivendo informazioni nel log attività in punti chiave. Questa tecnica è particolarmente utile quando si esegue un pacchetto VSPackage in un ambiente di vendita al dettaglio. Per altre informazioni, vedere [Procedura: Usare il Log attività](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Usare i simboli pubblici.  
  
     Per migliorare la leggibilità durante il debug, è possibile collegare i simboli del debugger.  
  
    1.  Dal **Strumenti/opzioni** dal menu passare alle **debug/simboli** nella finestra di dialogo.  
  
    2.  Aggiungere quanto segue **percorso del file (con estensione pdb) di simboli**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Per migliorare le prestazioni, specificare una cartella della cache di simboli, ad esempio:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere i problemi di un pacchetto VSPackage mancano o una delle relative dipendenze  
  
1. Per codice gestito, assicurarsi che i percorsi di riferimento siano corretti.  
  
   1.  Scegliere **Proprietà** dal menu **Progetto**.  
  
   2.  Selezionare il **riferimenti** scheda le **pagine delle proprietà** nella finestra di dialogo e assicurarsi che tutti i percorsi siano corretti. In alternativa, è possibile usare la **Visualizzatore oggetti** per cercare gli oggetti di riferimento.  
  
        Per codice gestito, è possibile usare la [Fuslogvw.exe (Visualizzatore registro associazione Assembly)](http://msdn.microsoft.com/library/e32fa443-0778-4cc3-bf36-5c8ea297d296) per visualizzare i dettagli di caricamenti di assembly non riuscita.  
  
2. Per codice non gestito, trovare il CLSID del pacchetto VSPackage nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nodo del Registro di sistema CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<version>* \CLSID  
  
   Assicurarsi che la voce InprocServer32 abbia il percorso corretto della dll VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
