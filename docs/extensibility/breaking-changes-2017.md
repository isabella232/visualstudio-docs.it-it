---
title: Modifiche di rilievo nell'estendibilità di Visual Studio 2017
description: Informazioni sui dettagli tecnici sulle modifiche di rilievo apportate al modello di estendibilità in Visual Studio 2017 e su cosa è possibile fare per risolvere tali problemi.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 00158c527ba4e5ea084836c49c5a8b7f5ba95366
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051313"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifiche all'estendibilità di Visual Studio 2017

Visual Studio 2017 offre un'esperienza di installazione Visual Studio più veloce e leggera che riduce l'impatto di Visual Studio sui sistemi utente, offrendo agli utenti una maggiore scelta rispetto ai carichi di lavoro e alle funzionalità installati. [](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) Per supportare questi miglioramenti, sono state apportate modifiche al modello di estendibilità, incluse alcune modifiche di rilievo. Questo articolo descrive i dettagli tecnici di queste modifiche e le operazioni che è possibile eseguire per risolvere tali modifiche.

> [!NOTE]
> Alcune informazioni sono dettagli di implementazione tempor volta e possono essere modificate in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che influiscono sul formato e sull'installazione di VSIX

Visual Studio 2017 ha introdotto il formato VSIX v3 (versione 3) per supportare l'esperienza di installazione leggera.

Le modifiche al formato VSIX includono:

* Dichiarazione dei prerequisiti di installazione. Per offrire agli utenti un'installazione Visual Studio semplice e veloce, il programma di installazione offre ora più opzioni di configurazione. Di conseguenza, per assicurarsi che le funzionalità e i componenti richiesti da un'estensione siano installati, le estensioni devono dichiarare le relative dipendenze.

  * Il Visual Studio 2017 offre automaticamente l'acquisizione e l'installazione dei componenti necessari per l'utente durante l'installazione dell'estensione.
  * Gli utenti vengono avvisati anche quando tentano di installare un'estensione che non è stata compilata usando il nuovo formato VSIX v3, anche se sono stati contrassegnati nel manifesto come destinazione della versione 15.0.

* Funzionalità avanzate per il formato VSIX. Per garantire [](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) un'installazione a basso impatto di Visual Studio che supporta anche le installazioni side-by-side, la maggior parte dei dati di configurazione non viene più salvato nel Registro di sistema e sono stati spostati assembly specifici di Visual Studio dalla Global Assembly Cache. Sono inoltre aumentate le funzionalità del formato VSIX e del motore di installazione VSIX, consentendo di usarlo invece di un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

Le nuove funzionalità includono:

* Registrazione nell'istanza Visual Studio specificata.
* Installazione all'esterno [della cartella extensions](set-install-root.md).
* Rilevamento dell'architettura del processore.
* Dipendenza dai Language Pack separati dalla lingua.
* L'installazione [con NGEN supporta](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Creare un'estensione per Visual Studio 2017

Gli strumenti di progettazione per la creazione del nuovo formato manifesto VSIX v3 sono disponibili Visual Studio 2017. Per informazioni dettagliate sull'uso degli strumenti di progettazione o sull'esecuzione di aggiornamenti manuali al progetto e al manifesto per sviluppare estensioni VSIX v3, vedere il documento relativo a Procedura: Eseguire la migrazione di progetti di estendibilità [a Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="change-visual-studio-user-data-path"></a>Modifica: Visual Studio percorso dati utente

In precedenza, in ogni computer poteva esistere Visual Studio una sola installazione di ogni versione principale di . Per supportare le installazioni side-by-side di Visual Studio 2017, possono esistere più percorsi dati utente per Visual Studio nel computer dell'utente.

Il codice in esecuzione Visual Studio processo deve essere aggiornato per usare Visual Studio Impostazioni Manager. Il codice in esecuzione all'esterno Visual Studio processo può trovare il percorso utente di un'installazione Visual Studio seguendo [le indicazioni riportate qui.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>Modifica: Global Assembly Cache (GAC)

La Visual Studio di base non viene più installata nella Global Assembly Cache. Le modifiche seguenti sono state apportate in modo che il codice in Visual Studio processo possa comunque trovare gli assembly necessari in fase di esecuzione.

> [!NOTE]
> [INSTALLDIR] di seguito fa riferimento alla directory radice di installazione di Visual Studio. *VSIXInstaller.exe* popolamento automatico, ma per scrivere codice di distribuzione personalizzato, leggere l'Visual Studio [.](locating-visual-studio.md)

* Assembly che sono stati installati solo nella GaC:

  Questi assembly sono ora installati in <em>[INSTALLDIR]\Common7\IDE \* , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> o *[INSTALLDIR]\Common7\IDE\PrivateAssemblies*. Queste cartelle fanno parte dei percorsi Visual Studio di probe del processo.

* Assembly installati in un percorso senza probe e nella GaC:

  * La copia nella Global Assembly Cache è stata rimossa dal programma di installazione.
  * È stato aggiunto un file con estensione *pkgdef* per specificare una voce della base di codice per l'assembly.

    Esempio:

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    In fase di esecuzione, il sottosistema Visual Studio pkgdef unisce queste voci nel file di configurazione di runtime del processo Visual Studio (in *[VSAPPDATA]\devenv.exe.config*) come [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementi. Questo è il modo consigliato per consentire al processo Visual Studio trovare l'assembly, perché evita la ricerca nei percorsi di probe.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Se l'estensione è in esecuzione all'interno del Visual Studio processo:

  * Il codice sarà in grado di trovare Visual Studio core.
  * È consigliabile usare un file con estensione *pkgdef* per specificare un percorso degli assembly, se necessario.

* Se l'estensione è in esecuzione all'esterno Visual Studio processo:

  Provare Visual Studio cercare gli assembly di base in <em>[INSTALLDIR]\Common7\IDE \* , *[INSTALLDIR]\Common7\IDE\PublicAssemblies</em> o *[INSTALLDIR]\Common7\IDE\PrivateAssemblies* usando il file di configurazione o il sistema di risoluzione degli assembly.

## <a name="change-reduce-registry-impact"></a>Modifica: ridurre l'impatto del Registro di sistema

### <a name="global-com-registration"></a>Registrazione COM globale

* In precedenza, Visual Studio molte chiavi del Registro di sistema negli hive HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE per supportare la registrazione COM nativa. Per eliminare questo impatto, Visual Studio ora usa [l'attivazione](/previous-versions/dotnet/articles/ms973913(v=msdn.10))senza registrazione per i componenti COM.
* Di conseguenza, la maggior parte dei file TLB/OLB/DLL in %ProgramFiles(x86)%\Common Files\Microsoft Shared\MSEnv non viene più installata per impostazione predefinita per Visual Studio. Questi file vengono ora installati in [INSTALLDIR] con Registration-Free manifesti COM usati dal Visual Studio processo host.
* Di conseguenza, il codice esterno basato sulla registrazione COM globale Visual Studio interfacce COM non troverà più queste registrazioni. Il codice in esecuzione Visual Studio processo non noterà alcuna differenza.

### <a name="visual-studio-registry"></a>Visual Studio registro

* In precedenza Visual Studio molte chiavi del Registro  di sistema negli hive HKEY_LOCAL_MACHINE e **HKEY_CURRENT_USER** del sistema in una chiave Visual Studio specifica:

  * **HKLM\Software\Microsoft\VisualStudio \{ Version}**: chiavi del Registro di sistema create dai programmi di installazione msi e dalle estensioni per computer.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version}**: chiavi del Registro di sistema create Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version}_Config:** una copia della chiave HKLM Visual Studio precedente, oltre alle chiavi del Registro di sistema unite dai file con estensione *pkgdef* in base alle estensioni.

* Per ridurre l'impatto sul Registro di sistema, Visual Studio ora usa la funzione [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) per archiviare le chiavi del Registro di sistema in un file binario privato in *[VSAPPDATA]\privateregistry.bin*. Solo un numero molto ridotto di Visual Studio chiavi specifiche rimangono nel Registro di sistema.
* Il codice esistente in esecuzione all'Visual Studio non è in alcun modo. Visual Studio reindirizza tutte le operazioni del Registro di sistema nella chiave Visual Studio HKCU al registro privato. La lettura e la scrittura in altri percorsi del Registro di sistema continueranno a usare il Registro di sistema.
* Il codice esterno dovrà caricare e leggere da questo file per Visual Studio del Registro di sistema.

### <a name="react-to-this-breaking-change"></a>React a questa modifica di rilievo

* Il codice esterno deve essere convertito per usare Registration-Free anche per i componenti COM.
* I componenti esterni possono trovare il percorso Visual Studio [seguendo le indicazioni riportate qui.](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)
* È consigliabile che i componenti esterni [usino External Impostazioni Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) invece di leggere/scrivere direttamente Visual Studio del Registro di sistema.
* Controllare se i componenti in uso dall'estensione potrebbero aver implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni del debugger possono sfruttare i vantaggi della nuova registrazione COM del [file JSON msvsmon](migrate-debugger-COM-registration.md).