---
title: Risoluzione dei problemi relativi ai pacchetti VSPackage Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698921"
---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage
Di seguito sono riportati i problemi comuni che potrebbero verificarsi con il pacchetto VSPackage e suggerimenti per risolvere i problemi.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere i problemi di un pacchetto VSPackage che impedisce l'avvio di Visual StudioTo troubleshoot a VSPackage that keeps Visual Studio from starting

- Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria.

   Per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avviare l'avvio in modalità provvisoria, al prompt dei comandi digitare **devenv.exe /safemode**.

   Durante questo processo non vengono caricati pacchetti VSPackage ad eccezione dei pacchetti VSPackage inclusi in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere i problemi di un pacchetto VSPackage che non viene caricatoTo troubleshoot a VSPackage that does not load

1. Assicurarsi che si sta utilizzando la radice del Registro di sistema in cui è registrato il pacchetto VSPackage per l'esecuzione, in genere la radice del Registro di sistema sperimentale.

    Per ulteriori informazioni, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

2. Se il pacchetto VSPackage è destinato per l'esecuzione nella radice del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Registro di sistema sperimentale, assicurarsi che si esegue la versione sperimentale di .

    Per eseguire la versione sperimentale, digitare quanto segue in una finestra di comando: **devenv /rootsuffix exp**.

3. Controllare le voci del Registro di sistema VSPackage.

    Per ulteriori informazioni, vedere [registrazione di pacchetti VSPackage](registering-and-unregistering-vspackages.md) e [gestione di VSPackage](../extensibility/managing-vspackages.md).

4. Aprire la finestra **di** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] output dell'istanza di che non riesce a caricare il pacchetto VSPackage. Informazioni sul motivo per cui il pacchetto VSPackage non riesce a caricare potrebbero essere visualizzate in tale finestra.

   > [!NOTE]
   > Se si avvia la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sperimentale di dall'ambiente di sviluppo integrato (IDE), esaminare la finestra di **output** di entrambe le versioni.

5. Esaminare il registro attività.

    Per ulteriori informazioni, vedere [Procedura: utilizzare il log attività](../extensibility/how-to-use-the-activity-log.md).

6. Per ulteriori informazioni sulle eccezioni generate dall'IDE, scegliere **eccezioni** dal **Debug** menu per abilitare le eccezioni. Nella finestra di dialogo **Eccezioni** selezionare i tipi di eccezioni per i quali si desiderano ulteriori informazioni.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere i problemi di un pacchetto VSPackage che non si registraTo troubleshoot a VSPackage that does not register

1. Assicurarsi che l'assembly VSPackage si trova in un percorso attendibile. RegPkg non può registrare assembly in un percorso non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione di sicurezza .net predefinita. Anche se viene visualizzato un avviso ogni volta che un utente crea un progetto in un percorso non attendibile, la casella di controllo "Non visualizzare più questo messaggio" può impedire il ripetersi di questo avviso.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi relativi a un comando non visibile o che genera un errore quando si fa clic su un comando

1. Unire i comandi di menu nuovi o modificati e quelli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] già presenti nell'IDE digitando quanto segue al prompt dei comandi: **devenv /rootsuffix Exp /setup**.

2. Assicurarsi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che sia possibile trovare UI.dll per il pacchetto VSPackage.Make Sure that can find UI.dll for your VSPackage.

   1. Trovare il CLSID del pacchetto VSPackage nella sezione pacchetti del Registro di sistema:

        HKLM, Software, Microsoft\\Visual Studio*\<versione>* pacchetti

   2. Verificare che il percorso specificato dalla sottochiave SatelliteDll sia corretto.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere i problemi di un pacchetto VSPackage che si comporta in modo imprevistoTo troubleshoot a VSPackage that behaves unexpectedly

1. Impostare i punti di interruzione nel codice.

     I punti di avvio necessari per il debug sono il costruttore e il metodo di inizializzazione. È inoltre possibile impostare punti di interruzione nell'area che si desidera valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire nel debugger.

    1. Scegliere **Proprietà** dal menu **Progetto**.

    2. Nella finestra di dialogo **Pagine delle proprietà** selezionare la scheda Debug.On the Property Pages dialog box, select the **Debug** tab.

    3. Nella casella Argomenti della riga di comando digitare il suffisso radice dell'ambiente di sviluppo destinato al pacchetto VSPackage.In the **Command line arguments** box, type the root suffix of the development environment that your VSPackage targets. Ad esempio, per selezionare la build sperimentale, digitare: **/RootSuffix Exp**.

    4. Scegliere **Avvia** **debug** dal menu Debug oppure premere F5.

        > [!NOTE]
        > Se si esegue il debug di un progetto, creare o caricare un'istanza esistente del progetto.

2. Utilizzare il registro attività.

     Tracciare il comportamento di VSPackage scrivendo informazioni nel log attività nei punti chiave. Questa tecnica è particolarmente utile quando si esegue un pacchetto VSPackage in un ambiente di vendita al dettaglio. Per ulteriori informazioni, vedere [Procedura: utilizzare il log attività](../extensibility/how-to-use-the-activity-log.md).

3. Utilizzare simboli pubblici.

     Per migliorare la leggibilità durante il debug, è possibile collegare simboli al debugger.

    1. Dal menu **Strumenti/Opzioni,** accedere alla finestra di **dialogo Debug/Simboli.**

    2. Aggiungere il percorso del file di **simboli (con estensione pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Per migliorare le prestazioni, specificare una cartella della cache dei simboli, ad esempio:To improve performance, specify a symbol cache folder, for example:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere i problemi di un VSPackage mancante o una delle relative dipendenzeTo troubleshoot a missing VSPackage or one of its dependencies

1. Per il codice gestito, assicurarsi che i percorsi di riferimento siano corretti.

   1. Scegliere **Proprietà** dal menu **Progetto**.

   2. Selezionare la scheda **Riferimenti** nella finestra di dialogo **Pagine delle proprietà** e verificare che tutti i percorsi siano corretti. In alternativa, è possibile utilizzare il **Visualizzatore oggetti** per cercare gli oggetti di riferimento.

        Per il codice gestito, è possibile utilizzare [Fuslogvw.exe (Visualizzatore registro associazione assembly)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) per visualizzare i dettagli dei caricamenti di assembly non riusciti.

2. Per il codice non gestito, trovare il CLSID del pacchetto VSPackage nel nodo del Registro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di sistema CLSID:

    HKLM, Software, Microsoft\\Visual Studio*\<versione>* CLSID

   Assicurarsi che la voce InprocServer32 abbia il percorso corretto della dll VSPackage.

## <a name="see-also"></a>Vedere anche
- [Pacchetti VSPackage](../extensibility/internals/vspackages.md)
