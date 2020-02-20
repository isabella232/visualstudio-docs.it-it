---
title: Risoluzione dei problemi relativi ai pacchetti VSPackage | Microsoft Docs
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
ms.openlocfilehash: b092c910b0303a62289e75b168e39628cbd0314b
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476997"
---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono riportati i problemi comuni che potrebbero verificarsi con il pacchetto VSPackage e suggerimenti per risolvere i problemi.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere i problemi relativi a un pacchetto VSPackage che impedisce l'avvio di Visual Studio  
  
- Avviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria.  
  
     Per avviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità provvisoria, al prompt dei comandi digitare **devenv. exe/safemode**.  
  
     Durante questo processo non viene caricato alcun VSPackage, eccetto i pacchetti VSPackage inclusi con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere i problemi relativi a un pacchetto VSPackage che non viene caricato  
  
1. Assicurarsi di usare la radice del registro di sistema in cui il pacchetto VSPackage è registrato per l'esecuzione, in genere la radice del registro di sistema sperimentale.  
  
     Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
2. Se il pacchetto VSPackage è destinato all'esecuzione nella radice del registro di sistema sperimentale, assicurarsi di eseguire la versione sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Per eseguire la versione sperimentale, digitare quanto segue in una finestra di comando: **devenv/rootsuffix exp**.  
  
3. Controllare le voci del registro di sistema VSPackage.  
  
     Per ulteriori informazioni, vedere la pagina relativa alla [registrazione di pacchetti VSPackage](internals/registering-vspackages.md) e [gestione dei pacchetti VSPackage](../extensibility/managing-vspackages.md).  
  
4. Aprire la finestra di **output** dell'istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in cui si è verificato un errore durante il caricamento del pacchetto VSPackage. Le informazioni sui motivi per cui il pacchetto VSPackage non viene caricato potrebbero essere visualizzate in tale finestra.  
  
    > [!NOTE]
    > Se si avvia la versione sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dalla Integrated Development Environment di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (IDE), controllare la finestra di **output** di entrambe le versioni.  
  
5. Esaminare il log attività.  
  
     Per altre informazioni, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).  
  
6. Per ulteriori informazioni sulle eccezioni generate dall'IDE, fare clic su **eccezioni** nel menu **debug** per abilitare le eccezioni. Nella finestra di dialogo **eccezioni** selezionare i tipi di eccezioni per cui si desidera ottenere ulteriori informazioni.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere i problemi relativi a un pacchetto VSPackage che non viene registrato  
  
1. Verificare che l'assembly VSPackage si trovi in un percorso attendibile. RegPkg non è in grado di registrare gli assembly in un percorso non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione di sicurezza .NET predefinita. Sebbene venga visualizzato un avviso ogni volta che un utente crea un progetto in una posizione non attendibile, la casella di controllo "non visualizzare più questo messaggio" può impedire la riesecuzione di questo avviso.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi relativi a un comando non visibile o che genera un errore quando si fa clic su un comando  
  
1. Unire i comandi di menu nuovi o modificati e quelli già presenti nell'IDE digitando quanto segue al prompt dei comandi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]: **devenv/rootsuffix exp/setup**.  
  
2. Assicurarsi che [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] possa trovare UI. dll per il pacchetto VSPackage.  
  
    1. Trovare il CLSID del pacchetto VSPackage nella sezione pacchetti del registro di sistema:  
  
         HKLM\Software\Microsoft\Visual Studio\\ *\<versione >* \Packages  
  
    2. Verificare che il percorso specificato dalla sottochiave SatelliteDll sia corretto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere i problemi relativi a un pacchetto VSPackage che si comporta in modo imprevisto  
  
1. Impostare i punti di interruzione nel codice.  
  
     I punti di partenza validi per il debug sono il costruttore e il metodo di inizializzazione. È anche possibile impostare punti di interruzione nell'area che si vuole valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire nel debugger.  
  
    1. Scegliere **Proprietà** dal menu **Progetto**.  
  
    2. Nella finestra di dialogo **pagine delle proprietà** selezionare la scheda **debug** .  
  
    3. Nella casella **argomenti della riga di comando** Digitare il suffisso radice dell'ambiente di sviluppo a cui è destinato il pacchetto VSPackage. Ad esempio, per selezionare la compilazione sperimentale, digitare: **/rootsuffix exp**.  
  
    4. Scegliere **Avvia debug** dal menu **debug** o premere F5.  
  
        > [!NOTE]
        > Se si esegue il debug di un progetto, creare o caricare ora un'istanza esistente del progetto.  
  
2. Usare il log attività.  
  
     Tracciare il comportamento VSPackage scrivendo le informazioni nel log attività nei punti chiave. Questa tecnica è particolarmente utile quando si esegue un pacchetto VSPackage in un ambiente di vendita al dettaglio. Per altre informazioni, vedere [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).  
  
3. Usare simboli pubblici.  
  
     Per migliorare la leggibilità durante il debug, è possibile aggiungere simboli al debugger.  
  
    1. Dal menu **Strumenti/Opzioni** passare alla finestra di dialogo **debug/simboli** .  
  
    2. Aggiungere il **percorso del file di simboli (con estensione pdb)** :  
  
         `https://msdl.microsoft.com/download/symbols`  
  
    3. Per migliorare le prestazioni, specificare una cartella della cache dei simboli, ad esempio:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere i problemi relativi a un VSPackage mancante o a una delle relative dipendenze  
  
1. Per il codice gestito, assicurarsi che i percorsi di riferimento siano corretti.  
  
   1. Scegliere **Proprietà** dal menu **Progetto**.  
  
   2. Selezionare la scheda **riferimenti** nella finestra di dialogo **pagine delle proprietà** e verificare che tutti i percorsi siano corretti. In alternativa, è possibile utilizzare il **Visualizzatore oggetti** per cercare gli oggetti a cui si fa riferimento.  
  
        Per il codice gestito, è possibile usare [Fuslogvw. exe (Visualizzatore log binding assembly)](https://msdn.microsoft.com/library/e32fa443-0778-4cc3-bf36-5c8ea297d296) per visualizzare i dettagli dei caricamenti di assembly non riusciti.  
  
2. Per il codice non gestito, trovare il CLSID del pacchetto VSPackage nel nodo del registro di sistema [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio\\ *\<versione >* \CLSID  
  
   Verificare che la voce InprocServer32 abbia il percorso corretto della dll del pacchetto VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
