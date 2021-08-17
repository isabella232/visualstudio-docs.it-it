---
title: Creazione di un software development kit | Microsoft Docs
description: Informazioni sull'infrastruttura generale degli SDK e su come creare un SDK di piattaforma e un SDK di estensione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b0543b280142747c9fdfdb9f6dfee87bb2f83da35b3f4ad539b685dd878ad1e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293560"
---
# <a name="create-a-software-development-kit"></a>Creare un Software Development Kit

Un Sdk (Software Development Kit) è una raccolta di API a cui è possibile fare riferimento come singolo elemento in Visual Studio. Nella **finestra di** dialogo Gestione riferimenti sono elencati tutti gli SDK rilevanti per il progetto. Quando si aggiunge un SDK a un progetto, le API sono disponibili in Visual Studio.

Esistono due tipi di SDK:

- Gli SDK della piattaforma sono componenti obbligatori per lo sviluppo di app per una piattaforma. Ad esempio, [!INCLUDE[win81](../debugger/includes/win81_md.md)] l'SDK è necessario per sviluppare [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

- Gli SDK di estensione sono componenti facoltativi che estendono una piattaforma, ma non sono obbligatori per lo sviluppo di app per tale piattaforma.

Le sezioni seguenti descrivono l'infrastruttura generale degli SDK e come creare un SDK di piattaforma e un SDK di estensione.

## <a name="platform-sdks"></a>Platform SDK

Gli SDK della piattaforma sono necessari per sviluppare app per una piattaforma. Ad esempio, [!INCLUDE[win81](../debugger/includes/win81_md.md)] l'SDK è necessario per sviluppare app per [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Installazione

Tutti gli SDK della piattaforma verranno installati in *HKLM\Software\Microsoft\Microsoft SDKs \\ [TPI]\v[TPV] \\ @InstallationFolder = [radice SDK]*. Di conseguenza, [!INCLUDE[win81](../debugger/includes/win81_md.md)] l'SDK viene installato in *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.*

### <a name="layout"></a>Layout

Gli SDK della piattaforma hanno il layout seguente:

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Nodo | Descrizione |
|------------------------| - |
| *Cartella Riferimenti* | Contiene file binari contenenti API che possono essere codificate. Possono includere file Windows metadati (WinMD) o assembly. |
| *Cartella DesignTime* | Contiene i file necessari solo in fase di pre-esecuzione/debug. Ad esempio documenti XML, librerie, intestazioni, file binari della fase di progettazione della casella degli strumenti, MSBuild elementi e così via<br /><br /> I documenti XML verrebbero inseriti idealmente nella cartella *\DesignTime,* ma i documenti XML per i riferimenti continueranno a essere inseriti insieme al file di riferimento in Visual Studio. Ad esempio, il documento XML per un riferimento <em>\References \\ [config] \\ [arch]\sample.dll</em> sarà *\References \\ [config] \\ [arch]\sample.xml* e la versione localizzata di tale documento sarà *\References \\ [config] \\ [arch] \\ [locale]\sample.xml*. |
| *Cartella di* configurazione | Possono essere presenti solo tre cartelle: *Debug*, *Retail* e *CommonConfiguration*. Gli autori dell'SDK possono inserire i file in *CommonConfiguration* se deve essere utilizzato lo stesso set di file SDK, indipendentemente dalla configurazione che verrà scelta come destinazione dal consumer dell'SDK. |
| *Cartella Architecture* | Può esistere *qualsiasi cartella* di architettura supportata. Visual Studio supporta le architetture seguenti: x86, x64, ARM e neutro. Nota: Win32 esegue il mapping a x86 e AnyCPU viene mappato a neutral.<br /><br /> MSBuild solo in *\CommonConfiguration\neutral* for Platform SDKs. |
| *SDKManifest.xml* | Questo file descrive come Visual Studio'SDK. Esaminare il manifesto dell'SDK per [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Valore visualizzato dal Visualizzatore oggetti nell'elenco Sfoglia .<br /><br /> **PlatformIdentity:** L'esistenza di questo attributo indica Visual Studio e MSBuild che l'SDK è un SDK della piattaforma e che i riferimenti aggiunti da esso non devono essere copiati in locale.<br /><br /> **TargetFramework:** Questo attributo viene usato dal Visual Studio per garantire che solo i progetti che hanno come destinazione gli stessi framework specificati nel valore di questo attributo possano utilizzare l'SDK.<br /><br /> **MinVSVersion:** Questo attributo viene usato Visual Studio per utilizzare solo gli SDK che si applicano a esso.<br /><br /> **Informazioni di riferimento:** Questo attributo deve essere specificato solo per i riferimenti che contengono controlli. Per informazioni su come specificare se un riferimento contiene controlli, vedere di seguito. |

## <a name="extension-sdks"></a>SDK di estensione

Le sezioni seguenti descrivono le operazioni da eseguire per distribuire un SDK di estensione.

### <a name="installation"></a>Installazione

Gli SDK di estensione possono essere installati per un utente specifico o per tutti gli utenti senza specificare una chiave del Registro di sistema. Per installare un SDK per tutti gli utenti, usare il percorso seguente:

*%Programmi%\Microsoft SDKs \<target platform\> \v<versione della piattaforma \> \ExtensionSDKs*

Per un'installazione specifica dell'utente, usare il percorso seguente:

*%USERPROFILE%\AppData\Local\Microsoft SDKs \<target platform\> \v<versione della piattaforma \> \ExtensionSDKs*

Se si vuole usare un percorso diverso, è necessario eseguire una delle due operazioni seguenti:

1. Specificarlo in una chiave del Registro di sistema:

     **HKLM\Software\Microsoft\Microsoft SDKs \<target platform> \v<versione della piattaforma \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     e aggiungere una sottochiave (predefinita) con valore `<path to SDK><SDKName><SDKVersion>` .

2. Aggiungere la MSBuild proprietà `SDKReferenceDirectoryRoot` al file di progetto. Il valore di questa proprietà è un elenco delimitato da punto e virgola delle directory in cui si trovano gli SDK di estensione a cui si vuole fare riferimento.

### <a name="installation-layout"></a>Layout di installazione

Gli SDK di estensione hanno il layout di installazione seguente:

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName<SDKVersion: il nome e la versione dell'SDK di estensione derivano dai nomi di cartella corrispondenti nel percorso della radice \> \\ \> dell'SDK. MSBuild usa questa identità per trovare l'SDK su disco e Visual Studio  questa identità viene visualizzata nella finestra Proprietà e nella finestra di dialogo **Gestione** riferimenti.

2. *Cartella* Riferimenti: i file binari che contengono le API. Possono essere file Windows metadati (WinMD) o assembly.

3. *Cartella redist:* i file necessari per il runtime/debug e devono essere in pacchetto come parte dell'applicazione dell'utente. Tutti i file binari devono essere posizionati sotto *\redist \\<config<\> \\ \> arch* e i nomi binari devono avere il formato seguente per garantire l'univocità: *]*. \<company> . \<product> \<purpose> . \<extension> <em>. Ad esempio, *Microsoft.Cpp.Build.dll</em>. Tutti i file con nomi che possono entrare in conflitto con i nomi di altri SDK (ad esempio, javascript, css, pri, xaml, png e jpg) devono essere posizionati sotto <em>\redist<config<arch<sdkname ad eccezione dei file associati ai controlli \\ \> \\ \> \\ \> \* XAML. Questi file devono essere posizionati sotto *\redist \\<config<arch<nome \> \\ \> \\ componente \> \\ </em>.

4. *Cartella DesignTime:* i file necessari solo in fase di pre-esecuzione/debug e che non devono essere in pacchetto come parte dell'applicazione dell'utente. Possono trattarsi di documenti XML, librerie, intestazioni, file binari della fase di progettazione della casella degli strumenti, MSBuild elementi e così via. Qualsiasi SDK destinato all'uso da parte di un progetto nativo deve avere un file *SDKName.props.* Di seguito è riportato un esempio di questo tipo di file.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    I documenti di riferimento XML vengono inseriti insieme al file di riferimento. Ad esempio, il documento di riferimento XML per l'assembly arch\sample.dlldi configurazione di \References<<*\\ \> \\ \><* è *\References \\<config<\> \\ arch \>\sample.xml* e la versione localizzata di tale documento è *\References<config<\\ arch<locale \> \\ \> \\ \>\sample.xml*.

5. *Cartella* di configurazione: tre sottocartelle: *Debug*, *Retail* e *CommonConfiguration*. Gli autori dell'SDK possono inserire i file in *CommonConfiguration* quando deve essere utilizzato lo stesso set di file SDK, indipendentemente dalla configurazione di destinazione del consumer dell'SDK.

6. *Cartella* Architecture: sono supportate le architetture seguenti: x86, x64, ARM, neutrale. Win32 esegue il mapping a x86 e AnyCPU esegue il mapping a neutral.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Il *fileSDKManifest.xml* descrive come Visual Studio usare l'SDK. Di seguito è riportato un esempio:

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

L'elenco seguente fornisce gli elementi del file :

1. DisplayName: valore visualizzato in Gestione riferimenti, Esplora soluzioni, Visualizzatore oggetti e altre posizioni nell'interfaccia utente per Visual Studio.

2. ProductFamilyName: nome complessivo del prodotto SDK. Ad esempio, l'SDK è denominato [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", che appartengono alla stessa famiglia di prodotti SDK, "Microsoft.WinJS". Questo attributo consente Visual Studio e MSBuild di stabilire tale connessione. Se questo attributo non esiste, come nome della famiglia di prodotti viene usato il nome dell'SDK.

3. FrameworkIdentity: specifica una dipendenza da una o più librerie Windows componenti. Il valore di questo attributo viene inserito nel manifesto dell'app che lo utilizza. Questo attributo è applicabile solo alle librerie Windows componenti.

4. TargetFramework: specifica gli SDK disponibili in Gestione riferimenti e nella casella degli strumenti. Elenco delimitato da punto e virgola dei moniker del framework di destinazione, ad esempio ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Se vengono specificate più versioni dello stesso framework di destinazione, Gestione riferimenti usa la versione più bassa specificata a scopo di filtro. Ad esempio, se ".NET Framework, version=v2.0; .NET Framework specificato version=v4.5.1", Gestione riferimenti userà ".NET Framework, version=v2.0". Se viene specificato un profilo del framework di destinazione specifico, solo tale profilo verrà utilizzato da Gestione riferimenti a scopo di filtro. Ad esempio, quando si specifica "Silverlight, version=v4.0, profile=WindowsPhone", Gestione riferimenti filtra solo il profilo Windows Phone; Un progetto che ha come destinazione la versione completa di Silverlight 4.0 Framework non visualizza l'SDK in Gestione riferimenti.

5. MinVSVersion: versione minima Visual Studio versione.

6. MaxPlatformVerson: la versione massima della piattaforma di destinazione deve essere usata per specificare le versioni della piattaforma in cui l'SDK di estensione non funzionerà. Ad esempio, il Microsoft Visual C++ Runtime Package v11.0 deve essere referenziato solo da Windows 8 progetto. Di conseguenza, Windows 8 maxPlatformVersion del progetto è 8.0. Ciò significa che Gestione riferimenti filtra Microsoft Visual C++ Runtime Package per un progetto Windows 8.1 e MSBuild genera un errore quando un progetto fa riferimento a [!INCLUDE[win81](../debugger/includes/win81_md.md)] esso. Nota: questo elemento è supportato a partire da [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: specifica gli SDK disponibili in Gestione riferimenti specificando i tipi di progetto Visual Studio applicabili. Vengono riconosciuti nove valori: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed e Native. L'autore dell'SDK può usare e ("+") o ("&#124;"), non ("!") operatori per specificare esattamente l'ambito dei tipi di progetto applicabili all'SDK.

    WindowsAppContainer identifica i progetti per le [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

8. SupportPrefer32Bit: i valori supportati sono "True" e "False". Il valore predefinito è "True". Se il valore è impostato su "False", MSBuild restituisce un errore per i progetti (o un avviso per i progetti desktop) se per il progetto che fa riferimento all'SDK è abilitato [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Prefer32Bit. Per altre informazioni su Prefer32Bit, vedere Pagina [Compilazione, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md) o [Compila, Project Designer (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: elenco delimitato da punto e virgola di architetture supportate dall'SDK. MSBuild viene visualizzato un avviso se l'architettura SDK di destinazione nel progetto di utilizzo non è supportata. Se questo attributo non viene specificato, MSBuild questo tipo di avviso non viene mai visualizzato.

10. SupportsMultipleVersions: se questo attributo è impostato su **Errore** o **Avviso,** MSBuild indica che lo stesso progetto non può fare riferimento a più versioni della stessa famiglia di SDK. Se questo attributo non esiste o è impostato **su** Consenti, MSBuild questo tipo di errore o avviso non viene visualizzato.

11. AppX: specifica il percorso dei pacchetti dell'app per la Windows di componenti sul disco. Questo valore viene passato al componente di registrazione della libreria Windows componente durante il debug locale. La convenzione di denominazione per il nome file *\<Company> è . . . \<Product> . . . \<Architecture> \<Configuration> \<Version> . appx*. La configurazione e l'architettura sono facoltative nel nome dell'attributo e nel valore dell'attributo se non si applicano alla libreria Windows componenti. Questo valore è applicabile solo alle librerie Windows componenti.

12. CopyRedistToSubDirectory: specifica dove devono essere copiati i file nella cartella *\redist* rispetto  alla radice  del pacchetto dell'app (ovvero il percorso del pacchetto scelto nella creazione guidata pacchetto app) e alla radice del layout di runtime. Il percorso predefinito è la radice del pacchetto dell'app e del layout **F5.**

13. DependsOn: elenco di identità dell'SDK che definiscono gli SDK da cui dipende questo SDK. Questo attributo viene visualizzato nel riquadro dei dettagli di Gestione riferimenti.

14. MoreInfo: URL della pagina Web che fornisce informazioni della Guida e altre informazioni. Questo valore viene usato nel collegamento Altre informazioni nel riquadro destro di Gestione riferimenti.

15. Tipo di registrazione: specifica la registrazione WinMD nel manifesto dell'app ed è necessario per WinMD nativo, che ha una DLL di implementazione controparte.

16. Riferimento al file: specificato solo per i riferimenti che contengono controlli o sono WinMD nativi. Per informazioni su come specificare se un riferimento contiene controlli, vedere Specificare la [posizione degli elementi della casella degli strumenti di](#ToolboxItems) seguito.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Specificare la posizione degli elementi della casella degli strumenti

**L'elemento ToolBoxItems** dello schema *SDKManifest.xml* specifica la categoria e la posizione degli elementi della casella degli strumenti negli SDK di piattaforma ed estensione. Gli esempi seguenti illustrano come specificare posizioni diverse. Ciò è applicabile ai riferimenti a WinMD o DLL.

1. Inserire i controlli nella categoria predefinita della casella degli strumenti.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Posizionare i controlli sotto un nome di categoria specifico.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Posizionare i controlli sotto nomi di categorie specifici.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Posizionare i controlli in nomi di categoria diversi in Blend e Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Enumerare controlli specifici in modo diverso in Blend e Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Enumerare controlli specifici e posizionarli sotto Visual Studio percorso comune o solo nel gruppo Tutti i controlli.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Enumerare controlli specifici e visualizzare solo un set specifico in ChooseItems senza che si presentino nella casella degli strumenti.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creare un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: Creare un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
