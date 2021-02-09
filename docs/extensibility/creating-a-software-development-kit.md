---
title: Creazione di un kit di sviluppo software | Microsoft Docs
description: Informazioni sull'infrastruttura generale degli SDK e su come creare una piattaforma SDK e un SDK di estensione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74e31cb8fddb00e8a6771a6ad3065bce57cc8bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902244"
---
# <a name="create-a-software-development-kit"></a>Creare una Software Development Kit

Un Software Development Kit (SDK) è una raccolta di API a cui è possibile fare riferimento come singolo elemento in Visual Studio. Nella finestra di dialogo **Gestione riferimenti** sono elencati tutti gli SDK rilevanti per il progetto. Quando si aggiunge un SDK a un progetto, le API sono disponibili in Visual Studio.

Esistono due tipi di SDK:

- Gli SDK della piattaforma sono componenti obbligatori per lo sviluppo di app per una piattaforma. Ad esempio, l' [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK è necessario per sviluppare [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

- Gli SDK di estensione sono componenti facoltativi che estendono una piattaforma, ma non sono obbligatori per lo sviluppo di app per tale piattaforma.

Le sezioni seguenti descrivono l'infrastruttura generale degli SDK e la modalità di creazione di un SDK di piattaforma e di estensione.

## <a name="platform-sdks"></a>Platform SDK

Gli SDK della piattaforma sono necessari per sviluppare app per una piattaforma. Ad esempio, l' [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK è necessario per sviluppare app per [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Installazione

Tutti gli SDK della piattaforma verranno installati in *HKLM\Software\Microsoft\Microsoft SDK \\ [TPI] \v [TPV] \\ @InstallationFolder = [radice SDK]*. Di conseguenza, l' [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK viene installato in *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout

Gli SDK della piattaforma hanno il seguente layout:

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
| Cartella *riferimenti* | Contiene file binari che contengono API che possono essere codificate in base a. Possono includere file o assembly di metadati Windows (WinMD). |
| Cartella *DesignTime* | Contiene i file necessari solo in fase di pre-esecuzione/debug. Questi possono includere documenti XML, librerie, intestazioni, binari della fase di progettazione della casella degli strumenti, elementi MSBuild e così via<br /><br /> I documenti XML dovrebbero, idealmente, essere posizionati nella cartella *\DesignTime* , ma i documenti XML per i riferimenti continueranno a essere inseriti insieme al file di riferimento in Visual Studio. Ad esempio, il documento XML per un riferimento <em>\References \\ [config] \\ [Arch] \sample.dll</em> sarà *\References \\ [config] \\ [Arch] \sample.xml* e la versione localizzata del documento sarà *\References \\ [config] \\ [Arch] \\ [locale] \sample.xml*. |
| Cartella di *configurazione* | Possono essere presenti solo tre cartelle: *debug*, *retail* e *CommonConfiguration*. Gli autori di SDK possono inserire i file in *CommonConfiguration* se è necessario usare lo stesso set di file SDK, indipendentemente dalla configurazione di destinazione del consumer SDK. |
| Cartella *Architecture* | È possibile che esista una cartella di *architettura* supportata. Visual Studio supporta le seguenti architetture: x86, x64, ARM e neutral. Nota: Win32 esegue il mapping a x86 e AnyCPU viene mappato a un neutro.<br /><br /> MSBuild cerca solo in *\CommonConfiguration\neutral* per Platform SDK. |
| *SDKManifest.xml* | In questo file viene descritto il modo in cui Visual Studio deve utilizzare l'SDK. Esaminare il manifesto dell'SDK per [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Valore visualizzato dall'Visualizzatore oggetti nell'elenco di esplorazione.<br /><br /> **PlatformIdentity:** L'esistenza di questo attributo indica a Visual Studio e MSBuild che SDK è un Platform SDK e che i riferimenti aggiunti non devono essere copiati localmente.<br /><br /> **TargetFramework:** Questo attributo viene utilizzato da Visual Studio per garantire che solo i progetti destinati agli stessi Framework specificati nel valore di questo attributo possano utilizzare l'SDK.<br /><br /> **MinVSVersion:** Questo attributo viene usato da Visual Studio per utilizzare solo gli SDK che vi si applicano.<br /><br /> **Riferimento:** Questo attributo deve essere specificato solo per i riferimenti che contengono controlli. Per informazioni su come specificare se un riferimento contiene controlli, vedere di seguito. |

## <a name="extension-sdks"></a>SDK di estensione

Nelle sezioni seguenti vengono descritte le operazioni necessarie per distribuire un SDK di estensione.

### <a name="installation"></a>Installazione

Gli SDK di estensione possono essere installati per un utente specifico o per tutti gli utenti senza specificare una chiave del registro di sistema. Per installare un SDK per tutti gli utenti, usare il percorso seguente:

*% Program%programmi%\Microsoft SDK \<target platform\> \v<numero di versione piattaforma \> \ExtensionSDKs*

Per un'installazione specifica dell'utente, usare il percorso seguente:

*%USERPROFILE%\AppData\Local\Microsoft SDK \<target platform\> \v<numero di versione della piattaforma \> \ExtensionSDKs*

Se si desidera utilizzare un percorso diverso, è necessario eseguire una delle due operazioni seguenti:

1. Specificarlo in una chiave del registro di sistema:

     **HKLM\Software\Microsoft\Microsoft SDK \<target platform> \v<numero di versione della piattaforma \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     e aggiungono una sottochiave (predefinita) con valore `<path to SDK><SDKName><SDKVersion>` .

2. Aggiungere la proprietà MSBuild `SDKReferenceDirectoryRoot` al file di progetto. Il valore di questa proprietà è un elenco delimitato da punti e virgola di directory in cui risiedono gli SDK di estensione a cui si vuole fare riferimento.

### <a name="installation-layout"></a>Layout di installazione

Gli SDK di estensione hanno il seguente layout di installazione:

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

1. \\<SDKName \> \\<SDKVersion \> : il nome e la versione dell'SDK di estensione sono derivati dai nomi di cartella corrispondenti nel percorso alla radice SDK. MSBuild usa questa identità per trovare l'SDK sul disco e Visual Studio Visualizza questa identità nella finestra **Proprietà** e nella finestra di dialogo **Gestione riferimenti** .

2. Cartella *riferimenti* : file binari che contengono le API. Questi possono essere file di metadati di Windows (WinMD) o assembly.

3. *Redist* Folder: i file necessari per la fase di esecuzione/debug e devono essere inseriti nel pacchetto come parte dell'applicazione dell'utente. Tutti i file binari devono essere posizionati sotto *redist \\<config \> \\<Arch \>* e i nomi binari devono avere il formato seguente per garantire l'univocità: *]* \<company> . \<product> . \<purpose> . \<extension> <em>. Ad esempio, * Microsoft.Cpp.Build.dll</em>. Tutti i file con nomi che possono essere in conflitto con i nomi di file di altri SDK (ad esempio, i file JavaScript, CSS, pri, XAML, PNG e jpg) devono essere posizionati sotto <em>redist \\<config \> \\<Arch \> \\<SDKName \> \* ad eccezione dei file associati ai controlli XAML. Questi file devono essere inseriti sotto * Redist \\<config \> \\<Arch \> \\<ComponentName \> \\ </em>.

4. Cartella *DesignTime* : i file necessari solo in fase di pre-esecuzione/debug e non devono essere inclusi nel pacchetto come parte dell'applicazione dell'utente. Si tratta di documenti XML, librerie, intestazioni, binari della fase di progettazione della casella degli strumenti, elementi MSBuild e così via. Qualsiasi SDK destinato all'utilizzo da un progetto nativo deve avere un file *SDKName. props* . Di seguito è riportato un esempio di questo tipo di file.

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

    I documenti di riferimento XML vengono posizionati insieme al file di riferimento. Ad esempio, il documento di riferimento XML per *\References \\<config \> \\<Arch \>\sample.dll* assembly è *\References \\<config \> \\<Arch \>\sample.xml* e la versione localizzata di tale documento è *\References \\<config<\> \\ Arch \> \\<impostazioni locali \>* \sample.xml.

5. Cartella di *configurazione* : tre sottocartelle: *debug*, *retail* e *CommonConfiguration*. Gli autori di SDK possono inserire i file in *CommonConfiguration* quando è necessario utilizzare lo stesso set di file SDK, indipendentemente dalla configurazione di destinazione del consumer SDK.

6. Cartella *Architecture* : sono supportate le architetture seguenti: x86, x64, ARM, Neutral. Win32 viene mappato a x86 e AnyCPU viene mappato a un neutro.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Nel file *SDKManifest.xml* viene descritto il modo in cui Visual Studio deve utilizzare l'SDK. Di seguito è riportato un esempio:

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

L'elenco seguente fornisce gli elementi del file:

1. DisplayName: valore visualizzato in Gestione riferimenti, Esplora soluzioni, Visualizzatore oggetti e altre posizioni nell'interfaccia utente di Visual Studio.

2. ProductFamilyName: il nome generale del prodotto SDK. Ad esempio, l' [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK è denominato "Microsoft. WinJS. 1.0" e "Microsoft. WinJS. 2.0", che appartengono alla stessa famiglia di prodotti SDK, "Microsoft. WinJS". Questo attributo consente a Visual Studio e a MSBuild di eseguire tale connessione. Se questo attributo non esiste, viene usato il nome dell'SDK come nome della famiglia di prodotti.

3. FrameworkIdentity: specifica una dipendenza da una o più librerie di componenti di Windows. Il valore di questo attributo viene inserito nel manifesto dell'applicazione consumer. Questo attributo è applicabile solo alle librerie di componenti di Windows.

4. TargetFramework: specifica gli SDK disponibili in Gestione riferimenti e nella casella degli strumenti. Si tratta di un elenco delimitato da punti e virgola di moniker del Framework di destinazione, ad esempio ".NET Framework, Version = v 2.0; .NET Framework, Version = v 4.5.1". Se vengono specificate diverse versioni dello stesso framework di destinazione, gestione riferimenti usa la versione specificata più bassa per scopi di filtraggio. Se, ad esempio, si specifica ".NET Framework, Version = v 2.0; .NET Framework, Version = v 4.5.1", gestione riferimenti userà ".NET Framework, Version = v 2.0". Se viene specificato un profilo del Framework di destinazione specifico, solo tale profilo verrà utilizzato da Gestione riferimenti per scopi di filtraggio. Ad esempio, quando si specifica "Silverlight, Version = v 4.0, profile = WindowsPhone", gestione riferimenti filtra solo il profilo Windows Phone; un progetto che ha come destinazione il framework Silverlight 4,0 completo non Visualizza l'SDK in Gestione riferimenti.

5. MinVSVersion: la versione minima di Visual Studio.

6. MaxPlatformVerson: è necessario usare la versione massima della piattaforma di destinazione per specificare le versioni della piattaforma in cui l'SDK di estensione non funzionerà. È ad esempio possibile fare riferimento al pacchetto di runtime di Microsoft Visual C++ v 11.0 solo dai progetti di Windows 8. Di conseguenza, il MaxPlatformVersion del progetto di Windows 8 è 8,0. Ciò significa che Gestione riferimenti filtra Microsoft Visual C++ pacchetto di runtime per un progetto Windows 8.1 e MSBuild genera un errore quando un [!INCLUDE[win81](../debugger/includes/win81_md.md)] progetto fa riferimento a tale pacchetto. Nota: questo elemento è supportato a partire da [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: specifica gli SDK disponibili in Gestione riferimenti specificando i tipi di progetto di Visual Studio applicabili. Vengono riconosciuti nove valori: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed e native. L'autore dell'SDK può usare e ("+") o ("&#124;"), not ("!") operatori per specificare esattamente l'ambito dei tipi di progetto che si applicano all'SDK.

    WindowsAppContainer identifica i progetti per le [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

8. SupportPrefer32Bit: i valori supportati sono "true" e "false". Il valore predefinito è "true". Se il valore è impostato su "false", MSBuild restituisce un errore per i [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] progetti (o un avviso per i progetti desktop) se il progetto che fa riferimento all'SDK è abilitato per Prefer32Bit. Per ulteriori informazioni su Prefer32Bit, vedere [pagina compilazione, creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md) o [pagina compilazione, progettazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: elenco delimitato da punti e virgola di architetture supportate dall'SDK. MSBuild Visualizza un avviso se l'architettura SDK di destinazione nel progetto che utilizza l'utilizzo non è supportata. Se questo attributo non è specificato, MSBuild non visualizzerà mai questo tipo di avviso.

10. SupportsMultipleVersions: se questo attributo è impostato su **Error** o **warning**, MSBuild indica che lo stesso progetto non può fare riferimento a più versioni dello stesso gruppo SDK. Se questo attributo non esiste o è impostato su **Consenti**, MSBuild non Visualizza questo tipo di errore o avviso.

11. AppX: specifica il percorso dei pacchetti dell'app per la libreria dei componenti di Windows sul disco. Questo valore viene passato al componente di registrazione della libreria dei componenti di Windows durante il debug locale. La convenzione di denominazione per il nome file è *\<Company> . \<Product> . \<Architecture> . \<Configuration> . \<Version> . appx*. La configurazione e l'architettura sono facoltative nel nome dell'attributo e nel valore dell'attributo se non si applicano alla libreria dei componenti di Windows. Questo valore è applicabile solo alle librerie di componenti di Windows.

12. CopyRedistToSubDirectory: specifica la posizione in cui devono essere copiati i file nella cartella *Redist* rispetto alla radice del pacchetto dell'app, ovvero il **percorso del pacchetto** scelto nella creazione guidata **pacchetto dell'applicazione** , e la radice del layout di Runtime. Il percorso predefinito è la radice del pacchetto dell'app e il layout di **F5** .

13. DependsOn: elenco di identità SDK che definiscono gli SDK da cui dipende questo SDK. Questo attributo viene visualizzato nel riquadro dei dettagli di gestione riferimenti.

14. MoreInfo: URL della pagina Web che fornisce la guida e altre informazioni. Questo valore viene utilizzato nel collegamento altre informazioni nel riquadro destro di gestione riferimenti.

15. Tipo di registrazione: specifica la registrazione WinMD nel manifesto dell'applicazione ed è necessaria per WinMD nativi, che ha una DLL di implementazione controparte.

16. Riferimento al file: specificato solo per i riferimenti che contengono controlli o sono file WinMD nativi. Per informazioni su come specificare se un riferimento contiene controlli, vedere [specificare il percorso degli elementi della casella degli strumenti riportati di](#ToolboxItems) seguito.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Specificare il percorso degli elementi della casella degli strumenti

L'elemento **ToolBoxItems** dello schema *SDKManifest.xml* specifica la categoria e la posizione degli elementi della casella degli strumenti negli SDK di piattaforma e di estensione. Negli esempi seguenti viene illustrato come specificare percorsi diversi. Questa operazione è applicabile ai riferimenti WinMD o DLL.

1. Posizionare i controlli nella categoria predefinita della casella degli strumenti.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Posizionare i controlli con un nome di categoria specifico.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Posizionare i controlli in nomi di categoria specifici.

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

5. Enumerare i controlli specifici in modo diverso in Blend e Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Enumerare i controlli specifici e posizionarli sotto il percorso comune di Visual Studio o solo nel gruppo tutti i controlli.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Enumerare controlli specifici e visualizzare solo un set specifico in ChooseItems senza che siano presenti nella casella degli strumenti.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: creare un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: creare un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
