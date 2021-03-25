---
title: Modifiche di rilievo nell'estensibilità di Visual Studio 2017
description: Informazioni sui dettagli tecnici sulle modifiche di rilievo apportate al modello di estendibilità in Visual Studio 2017 e sulle operazioni che è possibile eseguire per risolverli.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c07d48eb63c727701c3b6fcde9d405f9c96abec1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068193"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifiche all'estendibilità di Visual Studio 2017

Visual Studio 2017 offre un' [esperienza di installazione di Visual Studio più veloce e più leggera](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) che riduce l'impatto di Visual Studio sui sistemi utente, offrendo agli utenti una maggiore scelta rispetto ai carichi di lavoro e alle funzionalità installate. Per supportare questi miglioramenti, sono state apportate modifiche al modello di estendibilità, incluse alcune modifiche di rilievo. Questo articolo descrive i dettagli tecnici di queste modifiche e le operazioni che è possibile eseguire per risolverli.

> [!NOTE]
> Alcune informazioni sono dettagli di implementazione temporizzata e possono essere modificate in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che influiscono sul formato VSIX e sull'installazione

Visual Studio 2017 ha introdotto il formato VSIX V3 (versione 3) per supportare l'esperienza di installazione semplificata.

Le modifiche al formato VSIX includono:

* Dichiarazione dei prerequisiti di installazione. Per offrire un semplice e veloce installazione di Visual Studio, il programma di installazione offre ora più opzioni di configurazione per gli utenti. Di conseguenza, per garantire che le funzionalità e i componenti richiesti da un'estensione siano installati, le estensioni devono dichiararne le dipendenze.

  * Il programma di installazione di Visual Studio 2017 offre automaticamente l'acquisizione e l'installazione dei componenti necessari per l'utente durante l'installazione dell'estensione.
  * Gli utenti vengono avvisati anche quando si tenta di installare un'estensione che non è stata compilata con il nuovo formato VSIX V3, anche se sono stati contrassegnati nel manifesto come destinazione della versione 15,0.

* Funzionalità migliorate per il formato VSIX. Per offrire un' [installazione a basso impatto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) di Visual Studio che supporta anche installazioni affiancate, i dati di configurazione non vengono più salvati nel registro di sistema e gli assembly specifici di Visual Studio sono stati spostati fuori dalla GAC. Sono state anche migliorate le funzionalità del modulo VSIX e del motore di installazione VSIX, che consentono di usarle anziché un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

Le nuove funzionalità includono:

* Registrazione nell'istanza di Visual Studio specificata.
* Installazione al di fuori della [cartella Extensions](set-install-root.md).
* Rilevamento dell'architettura del processore.
* Dipendenza da Language Pack separati dal linguaggio.
* Installazione con [supporto NGen](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Compilare un'estensione per Visual Studio 2017

Gli strumenti di progettazione per la creazione del nuovo formato manifesto VSIX V3 sono disponibili in Visual Studio 2017. Per informazioni dettagliate sull'uso degli strumenti di progettazione o sull'esecuzione di aggiornamenti manuali del progetto e del manifesto per lo sviluppo di estensioni VSIX V3, vedere il documento allegato [procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

## <a name="change-visual-studio-user-data-path"></a>Modifica: percorso dati utente di Visual Studio

In precedenza, in ogni computer potrebbe esistere una sola installazione di ogni versione principale di Visual Studio. Per supportare installazioni affiancate di Visual Studio 2017, è possibile che nel computer dell'utente esistano più percorsi dati utente per Visual Studio.

Il codice in esecuzione all'interno del processo di Visual Studio deve essere aggiornato per usare Gestione impostazioni di Visual Studio. Il codice eseguito all'esterno del processo di Visual Studio consente di trovare il percorso utente di un'installazione di Visual Studio specifica [seguendo le istruzioni](locating-visual-studio.md)riportate qui.

## <a name="change-global-assembly-cache-gac"></a>Modifica: global assembly cache (GAC)

La maggior parte degli assembly principali di Visual Studio non vengono più installati nella GAC. Sono state apportate le modifiche seguenti affinché il codice in esecuzione nel processo di Visual Studio possa comunque trovare gli assembly necessari in fase di esecuzione.

> [!NOTE]
> [INSTALLDIR] di seguito si riferisce alla directory radice di installazione di Visual Studio. *VSIXInstaller.exe* compilerà automaticamente questo problema, ma per scrivere codice di distribuzione personalizzato, vedere la pagina relativa all' [individuazione di Visual Studio](locating-visual-studio.md).

* Assembly installati solo nella GAC:

  Questi assembly sono ora installati in <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies.</em> o *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*. Queste cartelle fanno parte dei percorsi di sondaggio del processo di Visual Studio.

* Assembly installati in un percorso non di probe e nella GAC:

  * La copia nella GAC è stata rimossa dal programma di installazione.
  * È stato aggiunto un file con *estensione pkgdef* per specificare una voce di base di codice per l'assembly.

    Ad esempio:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    In fase di esecuzione, il sottosistema pkgdef di Visual Studio unisce queste voci nel file di configurazione di runtime del processo di Visual Studio (in *[VSAPPDATA] \devenv.exe.config*) come [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementi. Questo è il modo consigliato per consentire al processo di Visual Studio di trovare l'assembly, perché evita la ricerca nei percorsi di probe.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Se l'estensione è in esecuzione all'interno del processo di Visual Studio:

  * Il codice sarà in grado di trovare gli assembly di base di Visual Studio.
  * Se necessario, provare a usare un file con *estensione pkgdef* per specificare il percorso degli assembly.

* Se l'estensione è in esecuzione all'esterno del processo di Visual Studio:

  Provare a cercare gli assembly principali di Visual Studio in <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies.</em> o *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* usando il file di configurazione o il resolver dell'assembly.

## <a name="change-reduce-registry-impact"></a>Modifica: ridurre l'effetto del registro di sistema

### <a name="global-com-registration"></a>Registrazione COM globale

* In precedenza, Visual Studio ha installato molte chiavi del registro di sistema nel HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE hive per supportare la registrazione COM nativa. Per eliminare questo impatto, Visual Studio USA ora l' [attivazione senza registrazione per i componenti com](/previous-versions/dotnet/articles/ms973913(v=msdn.10)).
* Di conseguenza, la maggior parte dei file TLB/OLB/DLL in% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv non vengono più installati per impostazione predefinita da Visual Studio. Questi file sono ora installati in [INSTALLDIR] con i manifesti Registration-Free COM corrispondenti utilizzati dal processo host di Visual Studio.
* Di conseguenza, il codice esterno che si basa sulla registrazione COM globale per le interfacce COM di Visual Studio non troverà più tali registrazioni. Il codice in esecuzione all'interno del processo di Visual Studio non vedrà una differenza.

### <a name="visual-studio-registry"></a>Registro di sistema di Visual Studio

* In precedenza, Visual Studio ha installato numerose chiavi del registro di sistema nel **HKEY_LOCAL_MACHINE** del sistema e **HKEY_CURRENT_USER** hive in una chiave specifica di Visual Studio:

  * **\Software\Microsoft\VisualStudio HKLM \{ Versione}**: chiavi del registro di sistema create dai programmi di installazione MSI e dalle estensioni per computer.
  * **HKCU\Software\Microsoft\VisualStudio \{ Versione}**: chiavi del registro di sistema create da Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * **HKCU\Software\Microsoft\VisualStudio \{ Versione} _Config**: una copia della chiave HKLM di Visual Studio precedente, oltre alle chiavi del registro di sistema unite da file *pkgdef* per estensioni.

* Per ridurre l'impatto sul Registro di sistema, Visual Studio USA ora la funzione [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) per archiviare le chiavi del registro di sistema in un file binario privato in *[VSAPPDATA] \privateregistry.bin*. Nel registro di sistema rimangono solo un numero molto ridotto di chiavi specifiche di Visual Studio.
* Il codice esistente in esecuzione all'interno del processo di Visual Studio non ha alcun impatto. In Visual Studio tutte le operazioni del registro di sistema vengono reindirizzate alla chiave specifica HKCU di Visual Studio nel registro di sistema privato. La lettura e la scrittura in altri percorsi del registro di sistema continueranno a usare il registro di sistema.
* Il codice esterno dovrà caricare e leggere da questo file le voci del registro di sistema di Visual Studio.

### <a name="react-to-this-breaking-change"></a>Rispondi a questa modifica di rilievo

* Il codice esterno deve essere convertito in modo da usare Registration-Free attivazione anche per i componenti COM.
* I componenti esterni possono trovare il percorso di Visual Studio [seguendo le istruzioni](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)riportate qui.
* È consigliabile che i componenti esterni usino [Gestione impostazioni esterne](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) anziché leggere/scrivere direttamente nelle chiavi del registro di sistema di Visual Studio.
* Controllare se i componenti utilizzati dall'estensione potrebbero avere implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni del debugger possono essere in grado di sfruttare i vantaggi della nuova [registrazione com msvsmon file JSON](migrate-debugger-COM-registration.md).