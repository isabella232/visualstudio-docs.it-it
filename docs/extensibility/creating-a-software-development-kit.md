---
title: Creazione di un Kit di Sviluppo Software Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739599"
---
# <a name="create-a-software-development-kit"></a>Creare un kit di sviluppo software

A software development kit (SDK) is a collection of APIs that you can reference as a single item in Visual Studio. Nella finestra di dialogo **Gestione riferimenti** sono elencati tutti gli SDK rilevanti per il progetto. Quando si aggiunge un SDK a un progetto, le API sono disponibili in Visual Studio.When you add an SDK to a project, the APIs are available in Visual Studio.

Esistono due tipi di SDK:

- Gli SDK della piattaforma sono componenti obbligatori per lo sviluppo di app per una piattaforma. Ad esempio, [!INCLUDE[win81](../debugger/includes/win81_md.md)] l'SDK [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] è necessario per sviluppare app.

- Gli SDK di estensione sono componenti facoltativi che estendono una piattaforma ma non sono obbligatori per lo sviluppo di app per tale piattaforma.

Le sezioni seguenti descrivono l'infrastruttura generale degli SDK e come creare un SDK della piattaforma e un SDK di estensione.

## <a name="platform-sdks"></a>SDK delle piattaforme

Gli SDK della piattaforma sono necessari per sviluppare app per una piattaforma. Ad esempio, [!INCLUDE[win81](../debugger/includes/win81_md.md)] l'SDK è [!INCLUDE[win81](../debugger/includes/win81_md.md)]necessario per sviluppare app per .

### <a name="installation"></a>Installazione

Tutti gli SDK della piattaforma verranno installati in *HKLM,\\Software, Microsoft Microsoft SDK\\ @InstallationFolder [TPI], v[TPV] , [radice SDK]*. Di conseguenza, l'SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)] viene installato in *HKLM, Software, Microsoft Microsoft SDKs, Windows v8.1*.

### <a name="layout"></a>Layout

Gli SDK della piattaforma hanno il layout seguente:Platform SDKs have the following layout:

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
| *Cartella Riferimenti* | Contiene i file binari che contengono API che possono essere codificati. Questi potrebbero includere i file di metadati di Windows (WinMD) o gli assembly. |
| *Cartella DesignTime* | Contiene i file necessari solo in fase di esecuzione/debugging. Questi potrebbero includere documenti XML, librerie, intestazioni, file binari della fase di progettazione della casella degli strumenti, elementi MSBuild e così via<br /><br /> I documenti XML, idealmente, verrebbero inseriti nella cartella *DesignTime,* ma i documenti XML per i riferimenti continueranno a essere inseriti accanto al file di riferimento in Visual Studio. Ad esempio, il documento XML per un riferimento<em>\\:References [config]\\[arch] ,sample.dll</em> sarà *"References\\[config]\\[arch] ,sample.xml*, e la versione localizzata di tale documento sarà *"References\\[config] [arch]\\\\[locale] .sample.xml*. |
| *Cartella di configurazione* | Possono essere presenti solo tre cartelle: *Debug*, *Retail* e *CommonConfiguration*. Gli autori SDK possono inserire i propri file in *CommonConfiguration* se lo stesso set di file SDK deve essere utilizzato, indipendentemente dalla configurazione di destinazione del consumer SDK. |
| *Cartella Architettura* | Qualsiasi cartella *dell'architettura* supportata può esistere. Visual Studio supporta le architetture seguenti: x86, x64, ARM e neutral. Nota: Win32 esegue il mapping a x86 e AnyCPU esegue il mapping a un neutro.<br /><br /> MSBuild cerca solo in *.* |
| *SDKManifest.xml (informazioni in linguaggio SDKManifest.xml)* | In questo file viene descritto come Visual Studio deve utilizzare l'SDK. Esaminare il manifesto [!INCLUDE[win81](../debugger/includes/win81_md.md)]SDK per :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Valore visualizzato dal Visualizzatore oggetti nell'elenco Sfoglia.<br /><br /> **PlatformIdentity:** L'esistenza di questo attributo indica a Visual Studio e MSBuild che l'SDK è un SDK della piattaforma e che i riferimenti aggiunti da esso non devono essere copiati localmente.<br /><br /> **Quadro di destinazione:** Questo attributo viene utilizzato da Visual Studio per garantire che solo i progetti destinati agli stessi framework specificati nel valore di questo attributo possano utilizzare l'SDK.<br /><br /> **VersioneMinVSVersion:** Questo attributo viene utilizzato da Visual Studio per utilizzare solo gli SDK che si applicano a esso.<br /><br /> **Riferimento:** Questo attributo deve essere specificato solo per i riferimenti che contengono controlli. Per informazioni su come specificare se un riferimento contiene controlli, vedere di seguito. |

## <a name="extension-sdks"></a>SDK di estensione

Le sezioni seguenti descrivono le operazioni da eseguire per distribuire un SDK di estensione.

### <a name="installation"></a>Installazione

Gli SDK di estensione possono essere installati per un utente specifico o per tutti gli utenti senza specificare una chiave del Registro di sistema. Per installare un SDK per tutti gli utenti, utilizzare il percorso seguente:

*%Programmi% Microsoft SDK piattaforma\<\>di destinazione .v\><numero di versione della piattaforma - ExtensionSDKs*

Per un'installazione specifica dell'utente, utilizzare il percorso seguente:For a user-specific installation, use the following path:

*%USERPROFILE%AppData Local Microsoft SDKs\<piattaforma\>di destinazione<\>numero di versione della piattaforma di piattaforma - ExtensionSDKs*

Se si desidera utilizzare una posizione diversa, è necessario eseguire una delle due operazioni seguenti:

1. Specificarlo in una chiave del Registro di sistema:

     **HKLM, Software, Microsoft Microsoft\<Microsoft Sdk, piattaforma di\>destinazione>,\<v<\<numero di versione della piattaforma, ovvero ExtensionSDKs , nome SDK>SDKVersion>**\

     e aggiungere una sottochiave (Predefinita) `<path to SDK><SDKName><SDKVersion>`con valore di .

2. Aggiungere la proprietà `SDKReferenceDirectoryRoot` MSBuild al file di progetto. Il valore di questa proprietà è un elenco delimitato da punti e virgola di directory in cui si trovano gli SDK di estensione a cui si desidera fare riferimento.

### <a name="installation-layout"></a>Layout di installazione

Gli SDK di estensione hanno il layout di installazione seguente:Extension SDKs have the following installation layout:

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

1. \\<SDKName\> \\<\>SDKVersion: il nome e la versione dell'SDK dell'estensione sono derivati dai nomi delle cartelle corrispondenti nel percorso della radice dell'SDK. MSBuild usa questa identità per trovare l'SDK su disco e Visual Studio visualizza questa identità nella finestra **Proprietà** e nella finestra di dialogo **Gestione riferimenti.**

2. *Cartella riferimenti:* i file binari che contengono le API. Questi potrebbero essere file di metadati di Windows (WinMD) file o assembly.

3. *Cartella Redist:* i file necessari per il runtime/debug e devono essere inclusi nel pacchetto come parte dell'applicazione dell'utente. Tutti i file binari devono essere posizionati sotto il valore di *\\<config\> \\<\>arch*e i nomi binari devono avere il seguente formato per garantire l'univocità: *]*\<società>. \<> del prodotto. \<> scopo. \<>di estensione <em>. Ad esempio, Microsoft.Cpp.Build.dll</em>. Tutti i file con nomi che possono collidere con nomi di file di altri SDK (ad esempio, javascript, css, pri, xaml, png e jpg) devono essere posizionati sotto il file <em>\\ .redist<\> \\ config\> \\<<'sdkname,\> \* ad eccezione dei file associati ai controlli XAML. Questi file devono essere posizionati\\ sotto\> \\ il\> \\ valore di\>configurazione del<redis<arch<componentname</em>.

4. *Cartella DesignTime:* i file necessari solo in fase di pre-esecuzione/debug e che non devono essere inclusi nel pacchetto come parte dell'applicazione dell'utente. Questi potrebbero essere documenti XML, librerie, intestazioni, file binari della fase di progettazione della casella degli strumenti, elementi MSBuild e così via. Qualsiasi SDK destinato all'utilizzo da parte di un progetto nativo deve disporre di un file *SDKName.props.* Di seguito viene illustrato un esempio di questo tipo di file.

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

    I documenti di riferimento XML vengono posizionati accanto al file di riferimento. Ad esempio, il documento di riferimento XML per la *configurazione\\ \> \\<riferimenti per<l'assembly arch\>-sample.dll* è *"References"\\<config\> \\<arch\>.sample.xml*e la versione localizzata di tale documento è *"References\\<config\> \\<arch\> \\<locale\>.sample.xml*.

5. *Cartella di configurazione:* tre sottocartelle: *Debug*, *Vendita al dettaglio*e *CommonConfiguration*. Gli autori SDK possono inserire i propri file in *CommonConfiguration* quando deve essere utilizzato lo stesso set di file SDK, indipendentemente dalla configurazione di destinazione del consumer SDK.

6. *Cartella Architettura:* sono supportate le seguenti architetture: x86, x64, ARM, neutro. Win32 esegue il mapping a x86 e AnyCPU esegue il mapping a un valore neutrale.

### <a name="sdkmanifestxml"></a>SDKManifest.xml (informazioni in linguaggio SDKManifest.xml)

Il file *SDKManifest.xml* descrive come Visual Studio deve utilizzare l'SDK. Di seguito è riportato un esempio:

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

1. DisplayName: il valore visualizzato in Gestione riferimenti, Esplora soluzioni, Visualizzatore oggetti e altri percorsi nell'interfaccia utente per Visual Studio.

2. ProductFamilyName: il nome complessivo del prodotto SDK. Ad esempio, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] l'SDK è denominato "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", che appartengono alla stessa famiglia di prodotti SDK, "Microsoft.WinJS". Questo attributo consente a Visual Studio e MSBuild di effettuare tale connessione. Se questo attributo non esiste, il nome SDK viene utilizzato come nome della famiglia di prodotti.

3. FrameworkIdentity: specifica una dipendenza da una o più librerie di componenti di Windows.FrameworkIdentity: Specifies a dependency on one or more Windows component libraries. Il valore di questo attributo viene inserito nel manifesto dell'app consumer. Questo attributo è applicabile solo alle librerie dei componenti di Windows.This attribute is applicable only to Windows component libraries.

4. TargetFramework: specifica gli SDK disponibili in Gestione riferimenti e nella casella degli strumenti. Si tratta di un elenco delimitato da punti e virgola di moniker del framework di destinazione, ad esempio ".NET Framework, version.v2.0; .NET Framework, version.v4.5.1". Se vengono specificate più versioni dello stesso framework di destinazione, Gestione riferimenti utilizza la versione specificata più bassa per scopi di filtro. Se, ad esempio, viene specificato ".NET Framework, version'v2.0; .NET Framework, version'v4.5.1", Reference Manager utilizzerà ".NET Framework, version'v2.0". Se viene specificato un profilo del framework di destinazione specifico, solo tale profilo verrà utilizzato da Gestione riferimenti per scopi di filtro. Ad esempio, quando viene specificato "Silverlight, version.v4.0, profile -WindowsPhone", Gestione riferimenti filtra solo il profilo di Windows Phone; un progetto destinato a Silverlight 4.0 Framework completo non vede l'SDK in Gestione riferimenti.

5. MinVSVersion: la versione minima di Visual Studio.

6. MaxPlatformVerson: la versione massima della piattaforma di destinazione deve essere usata per specificare le versioni della piattaforma su cui l'SDK di estensione non funzionerà. Ad esempio, i progetti di Windows 8 devono fare riferimento solo a Microsoft Visual C, Runtime Package v11.0. Pertanto, MaxPlatformVersion del progetto Windows 8 è 8.0. Ciò significa che Gestione riferimenti filtra il pacchetto di runtime di Microsoft Visual C, runtime [!INCLUDE[win81](../debugger/includes/win81_md.md)] per un progetto Windows 8.1 e MSBuild genera un errore quando un progetto fa riferimento. Nota: questo elemento [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]è supportato a partire da .

7. AppliesTo: specifica gli SDK disponibili in Gestione riferimenti specificando i tipi di progetto di Visual Studio applicabili. Vengono riconosciuti nove valori: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed e Native. L'autore dell'SDK può utilizzare e ("') o ("&#124;"), non ("!") operatori per specificare esattamente l'ambito dei tipi di progetto che si applicano all'SDK.

    WindowsAppContainer identifica [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] i progetti per le app.

8. SupportPrefer32Bit: i valori supportati sono "True" e "False". Il valore predefinito è "True". Se il valore è impostato su "False", [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] MSBuild restituisce un errore per i progetti (o un avviso per i progetti desktop) se il progetto che fa riferimento all'SDK ha Prefer32Bit abilitato. Per ulteriori informazioni su Prefer32Bit, vedere [pagina Compilazione, Progettazione progetti (C)](../ide/reference/build-page-project-designer-csharp.md) o [Pagina Compilazione, Progettazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: elenco delimitato da punti e virgola di architetture supportate dall'SDK. MSBuild visualizza un avviso se l'architettura SDK di destinazione nel progetto consumer non è supportata. Se questo attributo non è specificato, MSBuild non visualizza mai questo tipo di avviso.

10. SupportsMultipleVersions: se questo attributo è impostato su **Error** o **Warning**, MSBuild indica che lo stesso progetto non può fare riferimento a più versioni della stessa famiglia di SDK. Se questo attributo non esiste o è impostato su **Consenti**, MSBuild non visualizza questo tipo di errore o avviso.

11. AppX: specifica il percorso dei pacchetti dell'app per la libreria di componenti di Windows sul disco. Questo valore viene passato al componente di registrazione della libreria dei componenti di Windows durante il debug locale. La convenzione di denominazione per il nome del file è * \<Company>.\<> del prodotto. \<> dell'architettura. \<> di configurazione. Versione \<>.appx*. Configurazione e Architettura sono facoltative nel nome dell'attributo e nel valore dell'attributo se non si applicano alla libreria dei componenti di Windows.Configuration and Architecture are optional in the attribute name and the attribute value if they don't apply to the Windows component library. Questo valore è applicabile solo alle librerie dei componenti di Windows.This value is applicable only to Windows component libraries.

12. CopyRedistToSubDirectory: specifica dove devono essere copiati i file nella cartella *.redist* rispetto alla radice del pacchetto dell'app (ovvero il percorso del **pacchetto** scelto nella creazione guidata pacchetto **dell'app)** e la radice del layout di runtime. Il percorso predefinito è la radice del pacchetto dell'app e del layout **F5.**

13. DependsOn: elenco di identità SDK che definiscono gli SDK da cui dipende questo SDK. Questo attributo viene visualizzato nel riquadro dei dettagli di Gestione riferimenti.

14. MoreInfo: l'URL della pagina Web che fornisce assistenza e ulteriori informazioni. Questo valore viene utilizzato nel collegamento Ulteriori informazioni nel riquadro destro di Gestione riferimenti.

15. Tipo di registrazione: specifica la registrazione di WinMD nel manifesto dell'app ed è necessario per WinMD nativo, che ha una DLL di implementazione di controparte.

16. Riferimento al file: specificato solo per i riferimenti che contengono controlli o sono WinMD nativi. Per informazioni su come specificare se un riferimento contiene controlli, vedere [Specificare la posizione degli elementi della casella degli strumenti](#ToolboxItems) di seguito.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Specificare la posizione degli elementi della casella degli strumenti

L'elemento **ToolBoxItems** dello schema *SDKManifest.xml* specifica la categoria e il percorso degli elementi della casella degli strumenti negli SDK di piattaforma e di estensione. Negli esempi seguenti viene illustrato come specificare percorsi diversi. Ciò è applicabile ai riferimenti WinMD o DLL.

1. Posizionare i controlli nella categoria predefinita della casella degli strumenti.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Posizionare i controlli con un nome di categoria particolare.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Posizionare i controlli con nomi di categoria specifici.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Inserire i controlli con nomi di categoria diversi in Blend e Visual Studio.

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

6. Enumerare controlli specifici e inserirli nel percorso comune di Visual Studio o solo nel gruppo Tutti i controlli.

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

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creazione di un SDK con C](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procedura dettagliata: Creazione di un SDK con C .NET o Visual BasicWalkthrough: Create an SDK using C 'amp-Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
