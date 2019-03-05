---
title: Modifiche importanti all'estendibilità di Visual Studio 2017
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: e7363a0779721e4fb36106d6ee77324c341517ba
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324195"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Novità di estendibilità di Visual Studio 2017

Visual Studio 2017 offre un [esperienza di installazione di Visual Studio più veloce, leggero](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) che riduce l'impatto di Visual Studio nei sistemi utente e offre agli utenti più ampia su carichi di lavoro e le funzionalità installato. Per supportare questi miglioramenti, sono state apportate modifiche al modello di estendibilità, tra cui alcune modifiche di rilievo. Questo articolo descrive i dettagli tecnici di queste modifiche e ciò che è possibile eseguire per risolverli.

> [!NOTE]
> Alcune informazioni sono dettagli di implementazione di point-in-time e possono essere modificati in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che influiscono su installazione e formato VSIX

Visual Studio 2017 introdotto VSIX v3 formato (versione 3) per supportare l'esperienza di installazione leggero.

Le modifiche al formato VSIX includono:

* Dichiarazione dei prerequisiti di installazione. Per sfruttare il potenziale di un tipo semplice, fast-installazione di Visual Studio, il programma di installazione ora offre più opzioni di configurazione per gli utenti. Di conseguenza, per verificare che siano installati le funzionalità e i componenti richiesti da un'estensione, le estensioni devono dichiarare le relative dipendenze.

  * Il programma di installazione di Visual Studio 2017 offre automaticamente per acquisire e installare i componenti necessari per l'utente come parte dell'installazione dell'estensione.
  * Gli utenti vengono avvisati anche quando si tenta di installare un'estensione che non è stata creata usando il nuovo formato VSIX v3, anche se sono state contrassegnate nel relativo manifesto come destinato alla versione 15.0.

* Funzionalità avanzate per il formato VSIX. Per recapitare in una [installazione di basso impatto](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) di Visual Studio che supporta installazioni side-by-side, è non è più salvare la maggior parte dei dati di configurazione nel Registro di sistema e sono stati spostati assembly specifico di Visual Studio dalla Global Assembly Cache. È stata anche aumentata la funzionalità del formato VSIX e il motore di installazione VSIX, consentendo di usare, anziché un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

Le nuove funzionalità includono:

* Registrazione nell'istanza di Visual Studio specificata.
* Installazione di fuori di [cartella delle estensioni](set-install-root.md).
* Rilevamento di architettura del processore.
* Dipendenza da language separati language pack.
* Installazione con [supporto di NGEN](ngen-support.md).

## <a name="build-an-extension-for-visual-studio-2017"></a>Compilare un'estensione per Visual Studio 2017

Finestra di progettazione degli strumenti per la creazione del nuovo formato del manifesto VSIX v3 è disponibile in Visual Studio 2017. Vedere il documento associato [come: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) per informazioni dettagliate sull'utilizzo degli strumenti di progettazione o apportare manualmente gli aggiornamenti al progetto e manifesto per lo sviluppo di estensioni VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modifica: Percorso dei dati di Visual Studio utente

In precedenza, una singola installazione di ogni versione principale di Visual Studio possono essere presenti in ogni computer. Per supportare le installazioni side-by-side di Visual Studio 2017, potrebbero essere presenti più percorsi dati utente per Visual Studio nella macchina dell'utente.

Il codice in esecuzione all'interno del processo di Visual Studio deve essere aggiornato per usare le impostazioni di gestione di Visual Studio. Il codice in esecuzione all'esterno del processo di Visual Studio può trovare il percorso utente di un'installazione di Visual Studio specifica [seguendo le istruzioni riportate qui](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Modifica: Global Assembly Cache (GAC)

La maggior parte degli assembly principali di Visual Studio non vengono più installati nella GAC. Sono state apportate le modifiche seguenti in modo che il codice in esecuzione nel processo di Visual Studio può trovare ancora gli assembly necessari in fase di esecuzione.

> [!NOTE]
> [INSTALLDIR] di seguito fa riferimento alla directory radice di installazione di Visual Studio. *VSIXInstaller.exe* verrà inserito automaticamente, ma per scrivere il codice di distribuzione personalizzati, leggere [individuazione di Visual Studio](locating-visual-studio.md).

* Assembly che sono stati installati solo nella Global Assembly Cache:

   Questi assembly vengono ora installati sotto <em>[INSTALLDIR] \Common7\IDE.\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies.</em> oppure *\Common7\IDE\PrivateAssemblies. [INSTALLDIR]*. Queste cartelle fanno parte di percorsi di probe del processo di Visual Studio.

* Assembly che sono stati installati in un percorso probe non e Global Assembly Cache:

   * La copia nella Global Assembly Cache è stata rimossa dal programma di installazione.
   * Oggetto *pkgdef* file è stato aggiunto per specificare una voce di codebase dell'assembly.

      Ad esempio:

      ```xml
      [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
      "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
      "publicKeyToken"="Public Key Token"
      "culture"="neutral"
      "version"=15.0.0.0
      ```

      In fase di esecuzione, il sottosistema di Visual Studio pkgdef unisce queste voci nel file di configurazione di runtime del processo di Visual Studio (sotto *[VSAPPDATA]\devenv.exe.config*) come [ `<codeBase>` ](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) elementi. Questo è il modo consigliato per consentire il processo di Visual Studio a trovare l'assembly, in quanto evita la ricerca tramite percorsi di probe.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Se l'estensione è in esecuzione all'interno del processo di Visual Studio:

   * Il codice sarà in grado di trovare gli assembly di base di Visual Studio.
   * È consigliabile usare un *pkgdef* file per specificare un percorso agli assembly, se necessario.

* Se l'estensione è in esecuzione all'esterno del processo di Visual Studio:

   Prendere in considerazione alla ricerca di assembly principali di Visual Studio sotto <em>[INSTALLDIR] \Common7\IDE.\*, * [INSTALLDIR] \Common7\IDE\PublicAssemblies.</em> o *\Common7\IDE\PrivateAssemblies. [INSTALLDIR]* utilizzando il resolver di assembly o file di configurazione.

## <a name="change-reduce-registry-impact"></a>Modifica: Ridurre l'impatto del Registro di sistema

### <a name="global-com-registration"></a>Registrazione COM globale

* Visual Studio installato in precedenza, numero di chiavi del Registro di sistema nell'hive HKEY_LOCAL_MACHINE e HKEY_CLASSES_ROOT per supportare registrazione COM nativa. Per eliminare tale impatto, Visual Studio Usa ora [attivazione senza registrazione per i componenti COM](https://msdn.microsoft.com/library/ms973913.aspx).
* Di conseguenza, la maggior parte delle TLB / OLB / file DLL in % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv non vengono più installati per impostazione predefinita da Visual Studio. Questi file vengono ora installati in [INSTALLDIR] con manifesti di Registration-Free COM corrispondenti utilizzati dal processo host di Visual Studio.
* Di conseguenza, il codice esterno che si basa su registrazione COM globale per le interfacce COM di Visual Studio non sono più disponibili queste registrazioni. Codice in esecuzione nel processo di Visual Studio non visualizzerà una differenza.

### <a name="visual-studio-registry"></a>Registro di sistema di Visual Studio

* Visual Studio installato in precedenza, numero di chiavi del Registro di sistema al sistema **HKEY_LOCAL_MACHINE** e **HKEY_CURRENT_USER** hive in una chiave specifica di Visual Studio:

  * **HKLM\Software\Microsoft\VisualStudio\{Version}**: Chiavi del Registro di sistema create da programmi di installazione MSI ed estensioni per i singoli computer.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}**: Chiavi del Registro di sistema create da Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * **HKCU\Software\Microsoft\VisualStudio\{Version}_Config**: Una copia della chiave di Visual Studio HKLM precedente, oltre le chiavi del Registro di sistema dall'unione *pkgdef* file dalle estensioni.

* Per ridurre l'impatto sul Registro di sistema, Visual Studio Usa ora la [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) per archiviare le chiavi del Registro di sistema in un file binario privato nella funzione *[VSAPPDATA]\privateregistry.bin*. Solo un numero molto ridotto di chiavi specifico di Visual Studio rimane nel Registro di sistema.
* Il codice esistente in esecuzione all'interno del processo di Visual Studio non è compromessa. Visual Studio reindirizzerà tutte le operazioni del Registro di sistema nella chiave specifiche di HKCU Visual Studio nel Registro di sistema privato. Lettura e scrittura in altre posizioni del Registro di sistema continuerà a usare il Registro di sistema.
* Codice esterno sarà necessario caricare e leggere da questo file per le voci del Registro di sistema di Visual Studio.

### <a name="react-to-this-breaking-change"></a>Rispondere a questa modifica di rilievo

* Codice esterno deve essere convertito per utilizzare l'attivazione senza registrazione per nonché i componenti COM.
* Componenti esterni possono trovare il percorso di Visual Studio [seguendo le istruzioni riportate qui](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup).
* Si consiglia di usano i componenti esterni le [esterno Settings Manager](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) anziché la lettura/scrittura direttamente alle chiavi del Registro di sistema di Visual Studio.
* Controllare se i componenti che di estensione Usa hanno implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni del debugger possono essere in grado di sfruttare i vantaggi della nuova [msvsmon registrazione COM file JSON](migrate-debugger-COM-registration.md).
