---
title: Modifiche di rilievo nell'estensibilità di Visual Studio 2017Breaking Changes in Visual Studio 2017 extensibility
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739978"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifiche nell'estendibilità di Visual Studio 2017Changes in Visual Studio 2017 extensibility

Visual Studio 2017 offre un'esperienza di installazione di [Visual Studio più veloce](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) e leggera che riduce l'impatto di Visual Studio sui sistemi utente offrendo agli utenti una maggiore scelta sui carichi di lavoro e sulle funzionalità installate. Per supportare questi miglioramenti, sono state apportate modifiche al modello di estendibilità, incluse alcune modifiche di rilievo. Questo articolo descrive i dettagli tecnici di queste modifiche e cosa è possibile fare per affrontarle.

> [!NOTE]
> Alcune informazioni sono dettagli di implementazione temporizzata e possono essere modificate in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che interessano il formato VSIX e l'installazioneChanges affecting VSIX format and installation

Visual Studio 2017 ha introdotto il formato VSIX v3 (versione 3) per supportare l'esperienza di installazione leggera.

Le modifiche al formato VSIX includono:Changes to the VSIX format include:

* Dichiarazione dei prerequisiti di installazione. Per mantenere la promessa di un leggero, a installazione rapida di Visual Studio, il programma di installazione offre ora più opzioni di configurazione per gli utenti. Di conseguenza, per garantire che le funzionalità e i componenti richiesti da un'estensione siano installati, le estensioni devono dichiarare le dipendenze.

  * Il programma di installazione di Visual Studio 2017 offre automaticamente per acquisire e installare i componenti necessari per l'utente come parte dell'installazione dell'estensione.
  * Gli utenti vengono inoltre avvisati quando si tenta di installare un'estensione che non è stata compilata utilizzando il nuovo formato VSIX v3, anche se sono stati contrassegnati nel manifesto come versione di destinazione 15.0.Users are also warned when trying to install an extension that was not built using the new VSIX v3 format, even if they have been marked in their manifest as targeting version 15.0.

* Funzionalità avanzate per il formato VSIX. Per fornire [un'installazione a basso impatto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) di Visual Studio che supporta anche le installazioni side-by-side, non salviamo più la maggior parte dei dati di configurazione nel Registro di sistema e sono stati spostati gli assembly specifici di Visual Studio dalla Global Assembly Cache. Sono state inoltre aumentate le funzionalità del formato VSIX e del motore di installazione VSIX, consentendo di utilizzarlo anziché un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

Le nuove funzionalità includono:

* Registrazione nell'istanza di Visual Studio specificata.
* Installazione all'esterno della [cartella delle estensioni](set-install-root.md).
* Rilevamento dell'architettura del processore.
* Dipendenza dai Language Pack separati dalla lingua.
* Installazione con [supporto NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Creare un'estensione per Visual Studio 2017Build an extension for Visual Studio 2017

Gli strumenti di progettazione per la creazione del nuovo formato di manifesto VSIX v3 sono disponibili in Visual Studio 2017.Designer tooling for authoring of the new VSIX v3 manifest format is available in Visual Studio 2017. Vedere il documento di accompagnamento Procedura: eseguire la migrazione di progetti di [estendibilità a Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) per informazioni dettagliate sull'utilizzo degli strumenti di progettazione o l'esecuzione di aggiornamenti manuali per il progetto e il manifesto per sviluppare estensioni VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modifica: Percorso dati utente di Visual StudioChange: Visual Studio user data path

In precedenza, in ogni computer poteva esistere una sola installazione di ogni versione principale di Visual Studio. Per supportare le installazioni side-by-side di Visual Studio 2017, più percorsi di dati utente per Visual Studio possono esistere nel computer dell'utente.

Il codice in esecuzione all'interno del processo di Visual Studio deve essere aggiornato per usare Gestione impostazioni di Visual Studio.Code running inside the Visual Studio process should be updated to use the Visual Studio Settings Manager. Il codice in esecuzione all'esterno del processo di Visual Studio può trovare il percorso utente di un'installazione specifica di Visual Studio [seguendo le indicazioni riportate](locating-visual-studio.md)di seguito .

## <a name="change-global-assembly-cache-gac"></a>Modifica: Global Assembly Cache (GAC)

La maggior parte degli assembly di base di Visual Studio non sono più installati nella Global Assembly Cache. Le modifiche seguenti sono state apportate in modo che il codice in esecuzione nel processo di Visual Studio possa ancora trovare gli assembly necessari in fase di esecuzione.

> [!NOTE]
> [INSTALLDIR] di seguito si riferisce alla directory radice di installazione di Visual Studio. *VSIXInstaller.exe* verrà popolato automaticamente, ma per scrivere codice di distribuzione personalizzato, leggere [l'individuazione](locating-visual-studio.md)di Visual Studio .

* Assembly installati solo nella Global Assembly Cache:

  Questi assembly sono ora installati in <em>[INSTALLDIR], Common7,\*IDE , [INSTALLDIR], Common7, IDE, PublicAssemblies</em> o *[INSTALLDIR], Common7, IDE, PrivateAssemblies*. Queste cartelle fanno parte dei percorsi di sondaggio del processo di Visual Studio.These folders are part of the Visual Studio process's probing paths.

* Assembly installati in un percorso non di sondaggio e nella Global Assembly Cache:

  * La copia nella Global Assembly Cache è stata rimossa dall'installazione.
  * È stato aggiunto un file *con estensione pkgdef* per specificare una voce di base di codice per l'assembly.

    Ad esempio:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    In fase di esecuzione, il sottosistema pkgdef di Visual Studio unisce queste voci nel file di configurazione di runtime del [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) processo di Visual Studio (in *[VSAPPDATA]-devenv.exe.config*) come elementi. Questo è il modo consigliato per consentire al processo di Visual Studio di trovare l'assembly, perché evita la ricerca attraverso i percorsi di sondaggio.

### <a name="reacting-to-this-breaking-change"></a>Reagire a questo cambiamento di rottura

* Se l'estensione è in esecuzione all'interno del processo di Visual Studio:If your extension is running within the Visual Studio process:

  * Il codice sarà in grado di trovare gli assembly di base di Visual Studio.Your code will be able to find Visual Studio core assemblies.
  * Considerare l'utilizzo di un file *con estensione pkgdef* per specificare un percorso per gli assembly, se necessario.

* Se l'estensione è in esecuzione all'esterno del processo di Visual Studio:If your extension is running outside the Visual Studio process:

  Prendere in considerazione la possibilità di cercare gli assembly di base di Visual Studio in <em>[INSTALLDIR], Common7, IDE\*, ,[INSTALLDIR], Common7, IDE, PublicAssemblies</em> o *[INSTALLDIR], Common7, IDE, PrivateAssemblies* utilizzando il file di configurazione o il resolver di assembly.

## <a name="change-reduce-registry-impact"></a>Modifica: ridurre l'impatto del Registro di sistemaChange: Reduce registry impact

### <a name="global-com-registration"></a>Registrazione COM globale

* In precedenza, Visual Studio installato molte chiavi del Registro di sistema nel HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE hive per supportare la registrazione COM nativa. Per eliminare questo impatto, Visual Studio ora utilizza [l'attivazione senza registrazione per i componenti COM.](https://msdn.microsoft.com/library/ms973913.aspx)
* Di conseguenza, la maggior parte dei file TLB / OLB / DLL in %ProgramFiles(x86)% . Questi file vengono ora installati in [INSTALLDIR] con i corrispondenti manifesti COM senza registrazione utilizzati dal processo host di Visual Studio.
* Di conseguenza, il codice esterno che si basa sulla registrazione COM globale per le interfacce COM di Visual Studio non troverà più queste registrazioni. Il codice in esecuzione all'interno del processo di Visual Studio non noterà una differenza.

### <a name="visual-studio-registry"></a>Registro di sistema di Visual Studio

* In precedenza, Visual Studio installato molte chiavi del Registro di sistema nel HKEY_LOCAL_MACHINE del sistema e HKEY_CURRENT_USER in una chiave specifica di Visual Studio:Previously, Visual Studio installed many registry keys into the system's **HKEY_LOCAL_MACHINE** and **HKEY_CURRENT_USER** hives under a Visual Studio-specific key:

  * **HKLM: Software e versione\{di VisualStudio:** chiavi del Registro di sistema create dai programmi di installazione MSI e dalle estensioni per computer.
  * **HKCU Software Microsoft VisualStudio\{versione :** chiavi del Registro di sistema create da Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * **HKCU Software Microsoft VisualStudio\{versione _Config**: una copia della chiave HKLM di Visual Studio sopra riportata, più le chiavi del Registro di sistema unite dai file *con estensione pkgdef* dalle estensioni.

* Per ridurre l'impatto sul Registro di sistema, Visual Studio ora utilizza la funzione [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) per archiviare le chiavi del Registro di sistema in un file binario privato in *[VSAPPDATA]-privateregistry.bin*. Solo un numero molto ridotto di chiavi specifiche di Visual Studio rimangono nel Registro di sistema.
* Il codice esistente in esecuzione all'interno del processo di Visual Studio non è interessato. Visual Studio reindirizzerà tutte le operazioni del Registro di sistema nella chiave HKCU specifica di Visual Studio al Registro di sistema privato. La lettura e la scrittura in altri percorsi del Registro di sistema continueranno a utilizzare il Registro di sistema.
* Il codice esterno dovrà essere caricato e letto da questo file per le voci del Registro di sistema di Visual Studio.External code will need to load and read from this file for Visual Studio registry entries.

### <a name="react-to-this-breaking-change"></a>Reagisci a questo cambiamento di rottura

* Il codice esterno deve essere convertito per utilizzare l'attivazione senza registrazione anche per i componenti COM.
* I componenti esterni possono trovare il percorso di Visual Studio [seguendo le indicazioni riportate](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)di seguito.
* È consigliabile che i componenti esterni utilizzino [Gestione impostazioni esterne](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) anziché leggere/scrivere direttamente nelle chiavi del Registro di sistema di Visual Studio.
* Verificare se i componenti utilizzati dall'estensione potrebbero aver implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni del debugger potrebbero essere in grado di sfruttare la nuova registrazione COM del [file JSON msvsmon.](migrate-debugger-COM-registration.md)
