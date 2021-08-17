---
title: Creare un ambiente di compilazione con più computer
description: Creare un ambiente di compilazione all'interno dell'organizzazione installando Visual Studio in un computer host e quindi copiando vari file e impostazioni in un altro computer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6dcdf6b1b916a5f5f38137967d3d2a33072bca8f72d3ceb42b0b2ca27f7d6fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386537"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Procedura dettagliata: Creare un ambiente di compilazione con più computer

Per creare un ambiente di compilazione all'interno dell'organizzazione, è possibile installare Visual Studio in un computer host, quindi copiare i file e le impostazioni in un altro computer in modo che quest'ultimo possa partecipare alle compilazioni. Non è necessario installare Visual Studio nel secondo computer.

Questo documento non conferisce il diritto di ridistribuire il software esternamente o di fornire ambienti di compilazione a terze parti.

> Dichiarazione di non responsabilità<br /><br /> Questo documento viene offerto di base "così com'è". Mentre sono stati testati tutti i passi descritti, non è possibile testare in modo esaustivo ogni configurazione. Il documento verrà tenuto aggiornato il più possibile man mano che nuove informazioni saranno disponibili. Le informazioni e le indicazioni riportate nel presente documento, inclusi URL e altri riferimenti a siti Internet, sono soggette a modifica senza preavviso. Microsoft non riconosce alcuna garanzia, espressa o implicita, in merito alle informazioni qui fornite. L'utente accetta di usarle a proprio rischio.<br /><br /> Il presente documento non implica la concessione di alcun diritto di proprietà intellettuale in relazione ai prodotti Microsoft. Sono consentiti la copia e l'uso del presente documento a fini di riferimento interno.<br /><br /> Non vi è alcun obbligo di fornire a Microsoft suggerimenti, commenti o altri feedback ("Feedback") relativi al documento. Le informazioni immesse volontariamente possono tuttavia essere utilizzate per prodotti Microsoft e specifiche correlate o altre documentazioni ("Opzioni di Microsoft") che a loro volta possono essere utilizzate da terze parti per compilare i propri prodotti. Pertanto, se vengono forniti feedback a Microsoft su qualsiasi versione di questo documento o sulle opzioni Microsoft a cui questi si riferiscono, si accettano le condizioni seguenti: (a) Microsoft può liberamente utilizzare, riprodurre, distribuire, concedere in licenza o commercializzare i feedback in ogni opzione Microsoft; (b) si concedono inoltre a terze parti, senza spese, i diritti necessari per utilizzare o interfacciare altri prodotti con le opzioni Microsoft che incorporano i feedback; e (c) non dovranno mai essere forniti a Microsoft feedback (i) che violano qualsiasi brevetto, copyright o altre proprietà o diritti intellettuali di terze parti o (ii) altri termini di licenza che impongano di incorporare o derivare tali feedback nelle opzioni Microsoft o in altre proprietà intellettuali Microsoft, per concederne una licenza o condividerle con terze parti.

Questa procedura dettagliata è stata convalidata per i sistemi operativi seguenti:

- Windows 8 (x86 e x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Dopo aver completato i passaggi di questa procedura, è possibile utilizzare un ambiente multicomputer per compilare questi tipi di applicazioni:

- Applicazioni desktop C++ che utilizzano Windows 8 SDK
- Applicazioni desktop Visual Basic o C# destinate a .NET Framework 4.5

L'ambiente multicomputer non può essere utilizzato per compilare questi tipi di applicazioni:

- App UWP. Per compilare app UWP, è necessario installare Visual Studio nel computer di compilazione.
- Applicazioni desktop destinate a .NET Framework 4 o versioni precedenti. Per compilare questi tipi di applicazioni, è necessario installare Visual Studio o gli assembly e gli strumenti di riferimento di .NET (da Windows 7.1 SDK) nel computer di compilazione.

## <a name="prerequisites"></a>Prerequisiti

Visual Studio con il carico di lavoro **Sviluppo per desktop .NET** installato.

## <a name="install-software-on-the-computers"></a>Installare il software nei computer

Prima di tutto, configurare il computer host e quindi configurare il computer di compilazione.

Installando Visual Studio nel computer host, vengono creati i file e le impostazioni che verranno successivamente copiate nel computer di compilazione. È possibile installare Visual Studio in un computer x86 o x64, ma l'architettura del computer di compilazione deve corrispondere a quella del computer host.

1. Nel computer host installare Visual Studio.

2. Nel computer di compilazione installare .NET Framework 4.5 o versioni successive. Per verificare la corretta installazione, controllare che la voce **Version** nella sottochiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** del Registro di sistema sia impostata sul valore **4.5** o su uno maggiore.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Copiare i file dal computer host al computer di compilazione

In questa sezione viene descritta la copia di file specifici, compilatori, strumenti di compilazione, risorse di MSBuild e impostazioni del Registro di sistema dal computer host nel computer di compilazione. Queste istruzioni presuppongono che sia stato installato Visual Studio nel percorso predefinito nel computer host. In caso contrario, modificare i passaggi di conseguenza.

- In un computer x86 il percorso predefinito è *C:\Programmi\Microsoft Visual Studio*
- In un computer x64 il percorso predefinito è *C:\Programmi (x86)\Microsoft Visual Studio*

Si noti che il nome della cartella *Programmi* dipende dal sistema operativo installato. In un computer x86 il nome è *Programmi*, mentre in un computer x64 il nome è *Programmi (x86)*. Indipendentemente dall'architettura di sistema, in questa procedura si fa riferimento alla cartella *Programmi* come *%Programmi%*.

> [!NOTE]
> Nel computer di compilazione tutti i file rilevanti devono trovarsi nella stessa unità. La lettera dell'unità, tuttavia, può essere diversa dalla lettera dell'unità nel computer host in cui è installato Visual Studio. In ogni caso è necessario tener conto del percorso dei file quando si creano le voci del Registro di sistema come mostrato più avanti in questo documento.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Copiare i file di Windows SDK nel computer di compilazione

1. Se si dispone solo di Windows SDK per Windows 8, copiare queste cartelle in modo ricorsivo dal computer host nel computer di compilazione:

   - %Programmi%\Windows Kits\8.0\bin\

   - %Programmi%\Windows Kits\8.0\Catalogs\

   - %Programmi%\Windows Kits\8.0\DesignTime\

   - %Programmi%\Windows Kits\8.0\include\

   - %Programmi%\Windows Kits\8.0\Lib\

   - %Programmi%\Windows Kits\8.0\Redist\

   - %Programmi%\Windows Kits\8.0\References\

   Se si dispone anche di questi kit Windows 8...

   - Kit di valutazione e distribuzione di Microsoft Windows

   - Kit del driver per Microsoft Windows

   - Kit di certificazione hardware di Microsoft Windows

   ...alcuni file potrebbero essere installati nelle cartelle in *%Programmi%\Windows Kits\8.0* elencate nel passaggio precedente e le relative condizioni di licenza potrebbero non includere diritti di server di compilazione su tali file. Controllare le condizioni di licenza per ogni kit Windows installato per verificare se i file possono essere copiati nel computer di compilazione. Se le condizioni di licenza non consentono diritti di tipo server di compilazione, rimuovere i file dal computer di compilazione.

2. Copiare le seguenti cartelle in modo ricorsivo dal computer host nel computer di compilazione:

    - %Programmi%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %Programmi%\Common Files\Merge Modules\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\Tools\ProjectComponents\

    - %Programmi%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %Programmi%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

    - %Programmi%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. Copiare questi file dal computer host nel computer di compilazione:

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\Tools\vsvars32.bat

4. Le librerie di runtime di Visual C++ seguenti sono necessarie solo se si eseguono output di compilazione nel computer di compilazione, ad esempio come parte di un test automatizzato. I file si trovano in genere in sottocartelle nella cartella *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x86* o *%ProgramFiles%\Microsoft Visual Studio \\ \<version> \\ \<edition> \VC\redist\x64,* a seconda dell'architettura di sistema. Nei sistemi x86 copiare i file binari x86 nella cartella *\Windows\System32*. Nei sistemi x64 copiare i file binari x86 nella cartella *Windows\SysWOW64* e i file binari x64 nella cartella *Windows\System32*.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Copiare solo i seguenti file dalla cartella *Debug_NonRedist\x86* o *Debug_NonRedist\x64* al computer di compilazione, come descritto in [Preparare un computer per il test per l'esecuzione di un file eseguibile di debug](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Non deve essere copiato alcun altro file.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Creare le impostazioni del Registro di sistema

È necessario creare voci nel Registro di sistema per configurare le impostazioni di MSBuild.

1. Identificare la cartella padre per le voci del Registro di sistema. Tutte le voci del Registro di sistema vengono create nella stessa chiave padre. In un computer x86 la chiave padre è **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. In un computer x64 la chiave padre è **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Indipendentemente dall'architettura di sistema, in questa procedura dettagliata si fa riferimento alla chiave padre come %RegistryRoot%.

    > [!NOTE]
    > Se l'architettura del computer host differisce da quella del computer di compilazione, assicurarsi di utilizzare la chiave padre appropriata in ogni computer. Ciò è particolarmente importante se viene automatizzato il processo di esportazione.
    >
    > Inoltre, se nel computer di compilazione si utilizza una lettera di unità diversa da quella utilizzata nel computer host, assicurarsi di modificare di conseguenza i valori delle voci del Registro di sistema.

2. Creare le seguenti voci nel Registro di sistema del computer di compilazione. Tutte queste voci sono stringhe (Type == "REG_SZ" nel Registro di sistema). Impostare i valori di queste voci in modo analogo ai valori corrispondenti nel computer host.

   - **%RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **%RegistryRoot%\VisualStudio\11.0@Source Directories**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   In un computer di compilazione x64 creare anche la seguente chiave del Registro di sistema e fare riferimento al computer host per determinare come impostarla.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Se il computer di compilazione è x64 e si vuole usare la versione a 64 bit di MSBuild o se si usa il servizio di compilazione di Team Foundation Server in un computer x64, è necessario creare le voci seguenti nel Registro di sistema a 64 bit nativo. Fare riferimento al computer host per determinare come impostare queste voci.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Impostare le variabili di ambiente nel computer di compilazione

Per usare MSBuild nel computer di compilazione, è necessario impostare le variabili di ambiente PATH. È possibile usare *vcvarsall.bat* per impostare le variabili oppure configurarle manualmente.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Usare vcvarsall.bat per impostare le variabili di ambiente

Aprire una **finestra del prompt** dei comandi nel computer di compilazione ed eseguire *%Programmi%\Microsoft Visual Studio \\ \<version> \\ \<edition>\VC\vcvarsall.bat*. È possibile utilizzare un argomento della riga di comando per specificare il set di strumenti che si desidera utilizzare, ad esempio x86, x64 nativo o compilatore incrociato x64. Se non si specifica un argomento della riga di comando, viene utilizzato il set di strumenti x86.

Nella tabella seguente vengono descritti gli argomenti supportati di *vcvarsall.bat*:

|Argomento di vcvarsall.bat|Compilatore|Architettura del computer di compilazione|Architettura dell'output di compilazione|
| - |--------------| - | - |
|x86 (valore predefinito)|Nativo a 32 bit|x86, x64|x86|
|x86_amd64|x64 incrociato|x86, x64|x64|
|amd64|x64 nativo|x64|x64|

Se *vcvarsall.bat* viene eseguito correttamente, ovvero se non viene visualizzato alcun messaggio di errore, è possibile ignorare il passaggio successivo e passare alla sezione [Installare gli assembly di MSBuild nella Global Assembly Cache (GAC) nel computer di compilazione](#install-msbuild-to-gac) di questo documento.

### <a name="manually-set-environment-variables"></a>Impostare manualmente le variabili di ambiente

1. Per configurare manualmente l'ambiente dalla riga di comando, aggiungere il seguente percorso alla variabile di ambiente PATH:

    - %Programmi%\Microsoft Visual Studio \\ \<version> \\ \<edition> \Common7\IDE

2. Facoltativamente, è possibile aggiungere i seguenti percorsi alla variabile di ambiente PATH per rendere più facile l'utilizzo di MSBuild per compilare le soluzioni.

   Se si vuole usare MSBuild in modalità nativa a 32 bit, aggiungere questi percorsi alla variabile di ambiente PATH:

   - %Programmi%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Se si vuole usare MSBuild in modalità nativa a 64 bit, aggiungere questi percorsi alla variabile di ambiente PATH:

   - %Programmi%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" /> Installare gli assembly di MSBuild nella Global Assembly Cache (GAC) nel computer di compilazione

MSBuild richiede che siano installati assembly aggiuntivi nella GAC del computer di compilazione.

1. Copiare gli assembly seguenti dal computer host nel computer di compilazione. Poiché saranno installati nella GAC, la posizione nel computer di compilazione in cui verranno copiati non è rilevante.

    - %Programmi%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %Programmi%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %Programmi%\Microsoft Visual Studio \\ \<version> \\ \<edition>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Per installare assembly nella GAC, trovare *gacutil.exe* nel computer di compilazione. Tale file in genere si trova in %Programmi%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\. Se questa cartella non viene trovata, ripetere i passaggi illustrati nella sezione [Copiare i file dal computer host al computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) di questa procedura dettagliata.

     Aprire una finestra del **prompt dei comandi** con diritti amministrativi ed eseguire questo comando per ogni file:

     **gacutil -i \<file>**

    > [!NOTE]
    > Affinché un assembly venga installato completamente nella GAC, potrebbe essere necessario riavviare il computer.

## <a name="build-projects"></a>Compilare i progetti

È possibile utilizzare Azure Pipelines per compilare progetti e soluzioni di Visual Studio oppure è possibile compilarli dalla riga di comando. Quando si usa Azure Pipelines per compilare i progetti, viene richiamato il file eseguibile di MSBuild corrispondente all'architettura di sistema. Nella riga di comando è possibile usare MSBuild a 32 bit oppure a 64 bit ed è possibile scegliere l'architettura di MSBuild impostando la variabile di ambiente PATH o richiamando direttamente il file eseguibile specifico per l'architettura di MSBuild.

Per usare *msbuild.exe* al prompt dei comandi, eseguire il comando seguente, dove *soluzione.sln* è un segnaposto per il nome della soluzione.

**msbuild** *solution.sln*

Per altre informazioni su come usare MSBuild dalla riga di comando, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Creare l'ambiente di compilazione in modo che possa essere archiviato nel controllo del codice sorgente

È possibile creare un ambiente di compilazione che può essere distribuito in diversi computer e non richiede GAC per i file né la modifica di impostazioni del Registro di sistema. I seguenti passaggi sono solo uno dei modi per eseguire questa operazione. Questi passaggi devono essere adattati alle caratteristiche univoche del proprio ambiente di compilazione.

> [!NOTE]
> È necessario disabilitare la compilazione incrementale in modo che *tracker.exe* non generi un errore durante la compilazione. Per disabilitare la compilazione incrementale, impostare il seguente parametro di compilazione:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Creare una directory *Depot* sul computer host.

     Questi passaggi si riferiscono alla directory come %Depot%.

2. Copiare le directory e i file come descritto nella sezione [Copiare i file dal computer host al computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) di questa procedura dettagliata, eseguendo però la copia nella cartella *%Depot%* appena creata. Ad esempio, eseguire la copia da *%Programmi%\Windows Kits\8.0\bin* a *%Depot%\Windows Kits\8.0\bin*.

3. Quando i file vengono inseriti in *%Depot%*, apportare le seguenti modifiche:

    - In %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ e \Microsoft.CppCommon.targets\\ cambiare ogni istanza di

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         in

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         La prima denominazione si riferisce agli assembly di tipo GAC.

    - In %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets modificare ogni istanza di

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         in

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Creare un file con estensione *props*, ad esempio *Partner.AutoImports.props* e inserirlo nella cartella radice che contiene i progetti. Questo file viene utilizzato per impostare le variabili utilizzate da MSBuild per trovare le varie risorse. Se le variabili non sono impostate in questo file, vengono impostate da altri file con estensione *props* e *targets* che si basano sui valori del Registro di sistema. Poiché non viene impostato alcun valore del Registro di sistema, queste variabili potrebbero essere vuote e la compilazione potrebbe non riuscire. Aggiungere invece l'elemento seguente a *Partner.AutoImports.props*:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. In ognuno dei file di progetto, aggiungere la seguente riga all'inizio del file, dopo la riga `<Project Default Targets...>`.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Modificare l'ambiente dalla riga di comando nel modo seguente:

    - Impostare Depot=*percorso della directory Depot creata nel passaggio 1*

    - Impostare path=%path%;*percorso di MSBuild nel computer*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 15.0\Common7\IDE\

       Per una compilazione nativa a 64 bit, puntare alla versione a 64 bit di MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Modificare l'ambiente dalla riga di comando nel modo seguente:

    - Impostare Depot=*percorso della directory Depot creata nel passaggio 1*

    - Impostare path=%path%;*percorso di MSBuild nel computer*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 16.0\Common7\IDE\

       Per una compilazione nativa a 64 bit, puntare alla versione a 64 bit di MSBuild.

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Preparare un computer di test per l'esecuzione di un file eseguibile di debug](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)