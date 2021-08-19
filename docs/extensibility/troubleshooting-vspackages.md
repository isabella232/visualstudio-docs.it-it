---
title: Risoluzione dei problemi relativi ai pacchetti VSPackage | Microsoft Docs
description: Informazioni sui problemi comuni che possono verificarsi con il pacchetto VSPackage e suggerimenti per la risoluzione dei problemi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ac1ff1aff18aca87f94ad1b771766401254994c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110020"
---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi relativi ai pacchetti VSPackage
Di seguito sono riportati i problemi comuni che possono verificarsi con il pacchetto VSPackage e suggerimenti per risolverli.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere i problemi di un VSPackage che impedisce Visual Studio'avvio

- Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria.

   Per avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria, al prompt dei comandi digitare **devenv.exe /safemode**.

   Durante questo processo non vengono caricati vspackage ad eccezione dei vspackage inclusi in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere i problemi di un VSPackage che non viene caricato

1. Assicurarsi di usare la radice del Registro di sistema in cui è registrato il pacchetto VSPackage per l'esecuzione, in genere la radice sperimentale del Registro di sistema.

    Per altre informazioni, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

2. Se il pacchetto VSPackage è destinato all'esecuzione nella radice sperimentale del Registro di sistema, assicurarsi di eseguire la versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

    Per eseguire la versione sperimentale, digitare quanto segue in una finestra di comando: **devenv /rootsuffix exp**.

3. Controllare le voci del Registro di sistema VSPackage.

    Per altre informazioni, vedere [Registrazione di VSPackage e](registering-and-unregistering-vspackages.md) Gestione di [VSPackage.](../extensibility/managing-vspackages.md)

4. Aprire la **finestra Output** dell'istanza di che non riesce a caricare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage. Le informazioni sul motivo per cui il pacchetto VSPackage non viene caricato possono essere visualizzate in tale finestra.

   > [!NOTE]
   > Se si avvia la versione sperimentale di dall'ambiente di sviluppo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrato (IDE), esaminare la finestra **Output** di entrambe le versioni.

5. Esaminare il log attività.

    Per altre informazioni, vedere [Procedura: Usare il log attività](../extensibility/how-to-use-the-activity-log.md).

6. Per altre informazioni sulle eccezioni generate  dall'IDE, scegliere Eccezioni dal menu **Debug** per abilitare le eccezioni. Nella finestra **di dialogo** Eccezioni selezionare i tipi di eccezioni per cui si desiderano altre informazioni.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere i problemi relativi a un VSPackage che non esegue la registrazione

1. Assicurarsi che l'assembly VSPackage si trovi in un percorso attendibile. RegPkg non è in grado di registrare assembly in un percorso non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione di sicurezza .NET predefinita. Anche se viene visualizzato un avviso ogni volta che un utente crea un progetto in un percorso non attendibile, la casella di controllo "Non visualizzare più questo messaggio" può impedire che questo avviso si ripeta.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi di un comando non visibile o che genera un errore quando si fa clic su un comando

1. Unire i comandi di menu nuovi o modificati e quelli già presenti nell'IDE digitando quanto segue al prompt dei [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comandi: **devenv /rootsuffix Exp /setup**.

2. Assicurarsi che sia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] possibile trovare UI.dll per il pacchetto VSPackage.

   1. Trovare il CLSID del pacchetto VSPackage nella sezione Pacchetti del Registro di sistema:

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages

   2. Verificare che il percorso specificato dalla sottochiave SatelliteDll sia corretto.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere i problemi di un VSPackage che si comporta in modo imprevisto

1. Impostare i punti di interruzione nel codice.

     I punti di partenza per il debug sono il costruttore e il metodo di inizializzazione. È anche possibile impostare punti di interruzione nell'area da valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire nel debugger.

    1. Scegliere **Proprietà** dal menu **Progetto**.

    2. Nella finestra **di dialogo Pagine** delle proprietà selezionare la **scheda** Debug .

    3. Nella casella **Argomenti della riga di** comando digitare il suffisso radice dell'ambiente di sviluppo di destinazione del pacchetto VSPackage. Ad esempio, per selezionare la compilazione sperimentale, digitare: **/RootSuffix Exp**.

    4. Scegliere **Avvia** debug dal menu Debug **o** premere F5.

        > [!NOTE]
        > Se si esegue il debug di un progetto, creare o caricare un'istanza esistente del progetto.

2. Usare il log attività.

     Tracciare il comportamento di VSPackage scrivendo informazioni nel log attività nei punti chiave. Questa tecnica è particolarmente utile quando si esegue un VSPackage in un ambiente di vendita al dettaglio. Per altre informazioni, vedere [Procedura: Usare il log attività](../extensibility/how-to-use-the-activity-log.md).

3. Usare simboli pubblici.

     Per migliorare la leggibilità durante il debug, è possibile associare simboli al debugger.

    1. Dal menu **Strumenti/Opzioni** passare alla finestra **di dialogo Debug/Simboli.**

    2. Aggiungere questo **percorso del file di simboli (con estensione pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Per migliorare le prestazioni, specificare una cartella della cache dei simboli, ad esempio:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere i problemi relativi a un VSPackage mancante o a una delle relative dipendenze

1. Per il codice gestito, assicurarsi che i percorsi di riferimento siano corretti.

   1. Scegliere **Proprietà** dal menu **Progetto**.

   2. Selezionare la **scheda Riferimenti** nella finestra di dialogo **Pagine delle** proprietà e assicurarsi che tutti i percorsi siano corretti. In alternativa, è possibile usare il **Visualizzatore oggetti** per cercare gli oggetti a cui si fa riferimento.

        Per il codice gestito, è possibile usare il [Fuslogvw.exe (Visualizzatore](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) log associazione assembly) per visualizzare i dettagli dei caricamenti di assembly non riusciti.

2. Per il codice non gestito, trovare il CLSID del pacchetto VSPackage nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo del Registro di sistema CLSID:

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   Assicurarsi che la voce InprocServer32 abbia il percorso corretto della dll VSPackage.

## <a name="see-also"></a>Vedi anche
- [VSPackages](../extensibility/internals/vspackages.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
