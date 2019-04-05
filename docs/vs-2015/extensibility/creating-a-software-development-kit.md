---
title: Creazione di un Software Development Kit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a03611dcf06c5ecd7c2e638bdced6551bcb3a37
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969473"
---
# <a name="creating-a-software-development-kit"></a>Creazione di un Software Development Kit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un software development kit (SDK) è una raccolta di API che è possibile fare riferimento come un singolo elemento in Visual Studio. Il **gestione riferimenti** nella finestra di dialogo sono elencati tutti gli SDK pertinenti al progetto. Quando si aggiunge un SDK a un progetto, le API sono disponibili in Visual Studio.  
  
 Esistono due tipi di SDK:  
  
- SDK della piattaforma sono componenti obbligatori per lo sviluppo di App per una piattaforma. Ad esempio, il [!INCLUDE[win81](../includes/win81-md.md)] SDK è necessario per sviluppare [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app.  
  
- SDK di estensione sono componenti facoltativi estendono una piattaforma ma che non sono obbligatori per lo sviluppo di App per la piattaforma.  
  
  Le sezioni seguenti descrivono l'infrastruttura generale di SDK e come creare un SDK della piattaforma e un SDK di estensione.  
  
- [SDK di piattaforma](#PlatformSDKs)  
  
- [SDK di estensione](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> SDK di piattaforma  
 SDK della piattaforma sono necessari per sviluppare App per una piattaforma. Ad esempio, il [!INCLUDE[win81](../includes/win81-md.md)] SDK è necessario per sviluppare App per [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Installazione  
 Tutti gli SDK della piattaforma verranno installato al SDK HKLM\Software\Microsoft\Microsoft\\[TPI] \v [TPV]\\ @InstallationFolder = [radice SDK]. Di conseguenza, il [!INCLUDE[win81](../includes/win81-md.md)] SDK viene installato in HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Layout  
 Gli SDK di piattaforma saranno necessario lo schema seguente:  
  
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
  
|Nodo|Descrizione|  
|----------|-----------------|  
|Cartella riferimenti|Contiene i file binari che contengono le API che possono essere codificate a fronte. Questi possono includere i file di metadati Windows (WinMD) o assembly.|  
|Cartella DesignTime|Contiene i file che sono necessari solo in fase di pre-run/debug. Quali documenti XML, librerie, intestazioni, i file binari in fase di progettazione della casella degli strumenti, gli elementi di MSBuild e così via<br /><br /> Documentazione XML sarebbe, in teoria, trovarsi nella cartella \DesignTime, ma la documentazione XML per i riferimenti continuerà a essere inseriti accanto ai file di riferimento in Visual Studio. Ad esempio, il documento XML per un riferimento \References\\[configurazione]\\[arch]\sample.dll saranno \References\\[configurazione]\\[arch]\sample.xml e la versione localizzata di tale documentazione si troveranno \References\\[configurazione]\\[arch]\\[locale]\sample.xml.|  
|Cartella di configurazione|Possono essere presenti solo tre cartelle: il debug, vendita al dettaglio e CommonConfiguration. Se lo stesso set di file del SDK devono essere usati, indipendentemente dalla configurazione che sarà destinati al consumer SDK, è possono distribuire i file sotto CommonConfiguration gli autori SDK.|  
|Cartella di architettura|Può esistere una cartella qualsiasi architettura supportata. Visual Studio supporta le seguenti architetture: x86, x64, ARM e neutral. Nota: Esegue il mapping di Win32 per x86 e AnyCPU esegue il mapping a neutro.<br /><br /> MSBuild cerca solo in \CommonConfiguration\neutral SDK della piattaforma.|  
|SDKManifest.xml|Questo file illustra la procedura Visual Studio devono usare il SDK. Esaminare il manifesto SDK per [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Il valore che consente di visualizzare il Visualizzatore oggetti nell'elenco di ricerca.<br /><br /> **PlatformIdentity:** L'esistenza di questo attributo indica a Visual Studio e MSBuild che il SDK è un SDK della piattaforma e che i riferimenti aggiunti da quest'ultimo non devono essere copiati localmente.<br /><br /> **TargetFramework:** Questo attributo viene utilizzato da Visual Studio per garantire che solo i progetti che hanno come destinazione il Framework stesso come specificato nel valore di questo attributo può utilizzare il SDK.<br /><br /> **MinVSVersion:** Questo attributo viene utilizzato da Visual Studio per utilizzare solo gli SDK che si applicano a esso.<br /><br /> **Informazioni di riferimento:** Questo attributo deve essere specificato per solo tali riferimenti che contengono controlli. Per informazioni su come specificare se un riferimento contiene i controlli, vedere di seguito.|  
  
##  <a name="ExtensionSDKs"></a> SDK di estensione  
 Le sezioni seguenti descrivono ciò che è necessario eseguire per distribuire un SDK di estensione.  
  
### <a name="installation"></a>Installazione  
 SDK di estensione possono essere installati per un utente specifico o per tutti gli utenti senza specificare una chiave del Registro di sistema. Per installare un SDK per tutti gli utenti, usare il percorso seguente:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Per un'installazione specifica dell'utente, usare il percorso seguente:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Se si desidera usare un percorso diverso, è necessario eseguire una delle seguenti operazioni:  
  
1.  Specificata in una chiave del Registro di sistema:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     e aggiungere una sottochiave (impostazione predefinita) che ha un valore pari `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Aggiungere la proprietà MSBuild `SDKReferenceDirectoryRoot` al file di progetto. Il valore di questa proprietà è un elenco delimitato da punti semi delle directory in cui si trovano gli SDK di estensione si desidera fare riferimento.  
  
### <a name="installation-layout"></a>Layout di installazione  
 SDK di estensione hanno il layout di installazione seguenti:  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: il nome e la versione dell'estensione SDK è derivato dai nomi di cartella corrispondente nel percorso della directory radice SDK. MSBuild Usa questa identità per reperire il SDK su disco e Visual Studio visualizza l'identità nel **delle proprietà** finestra e **gestione riferimenti** finestra di dialogo.  
  
2.  Cartella Riferimenti: i file binari che contengono le API. Può trattarsi di file di metadati Windows (WinMD) o assembly.  
  
3.  Cartella Redist: i file necessari per il debug/runtime e devono ottenere incluso nel pacchetto come parte dell'applicazione dell'utente. Tutti i file binari devono essere inseriti sotto \redist\\< configurazione\>\\< arch\>, e i nomi binari devono avere il formato seguente per garantire l'univocità:  **\<aziendale >.\< Product >. \<scopo >. \<estensione >**. Ad esempio, Microsoft.Cpp.Build.dll. Tutti i file con nomi che siano in conflitto con nomi di file da altri SDK (ad esempio, i file javascript, css, pri, xaml, png e jpg) devono essere inseriti sotto \redist\\< configurazione\>\\< arch\> \\< sdkname\>\ tranne i file che sono associati a XAML controlla. Questi file devono essere posizionati sotto \redist\\< configurazione\>\\< arch\>\\< componentname\>\\.  
  
4.  La cartella DesignTime: i file che ne occorrono in unico pre-run/debug ora e non deve essere incluso nel pacchetto dell'applicazione dell'utente. Può trattarsi di documentazione XML, librerie, intestazioni, i file binari in fase di progettazione della casella degli strumenti, gli elementi di MSBuild e così via. Qualsiasi SDK di cui è previsto per il consumo da un progetto nativo deve essere presente un' *SDKName*file props. Di seguito viene illustrato un esempio di questo tipo di file.  
  
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
  
     I documenti di riferimento XML vengono inseriti accanto ai file di riferimento. Ad esempio, il documento di riferimento XML per il **\References\\< configurazione\>\\< arch\>\sample.dll** assembly è **\References\\ < file config\>\\< arch\>\sample.xml**, e la versione localizzata di tale documento viene **\References\\< configurazione\>\\< arch\>\\< impostazioni locali\>\sample.xml**.  
  
5.  Cartella di configurazione: tre sottocartelle: Debug delle vendite al dettaglio e CommonConfiguration. Gli autori SDK possono inserire i file sotto CommonConfiguration quando lo stesso set di file del SDK devono essere usati, indipendentemente dalla configurazione di destinazione da parte del consumer SDK.  
  
6.  Cartella di architettura: sono supportate le seguenti architetture: x86, x64, ARM, neutro. Esegue il mapping di Win32 per x86 e AnyCPU esegue il mapping a neutro.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Questo file illustra la procedura Visual Studio devono usare il SDK. Di seguito è riportato un esempio.  
  
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
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 L'elenco seguente offre gli elementi del file.  
  
1.  DisplayName: il valore visualizzato in Gestione riferimenti, Esplora soluzioni, Visualizzatore oggetti e in altre posizioni nell'interfaccia utente per Visual Studio.  
  
2.  ProductFamilyName: Il nome del prodotto SDK globale. Ad esempio, il [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK è denominata "Microsoft.WinJS.1.0" e "Microsoft.WinJS.2.0", che appartengono alla stessa famiglia della famiglia di prodotti SDK, "Microsoft.WinJS". Questo attributo consente a Visual Studio e MSBuild realizzare tale connessione. Se questo attributo non esiste, il nome del SDK viene utilizzato come il nome della famiglia di prodotti.  
  
3.  Formato di FrameworkIdentity: specifica una dipendenza da uno o più librerie dei componenti Windows che il valore di questo attributo viene inserito nel manifesto dell'app consumer. Questo attributo è applicabile solo per le librerie dei componenti di Windows.  
  
4.  TargetFramework: specifica gli SDK disponibili in Gestione riferimenti e casella degli strumenti. Questo è un elenco delimitato da punto e virgola di moniker del framework di destinazione, ad esempio ".NET Framework, versione = v2.0; .NET Framework, versione = v4.5.1". Se vengono specificate più versioni dello stesso framework di destinazione, gestione riferimenti Usa la versione minima specificata a scopo di filtro. Ad esempio, se ".NET Framework, versione = v2.0; .NET Framework, versione = v4.5.1" viene specificato, verrà utilizzato Gestione riferimenti ".NET Framework, versione = v2.0". Se viene specificato un profilo di framework di destinazione specifica, solo tale profilo verrà utilizzato da Gestione riferimenti a scopo di filtro. Ad esempio, quando "Silverlight, versione = v4.0, profilo = WindowsPhone" viene specificato, gestione riferimenti vengono applicati filtri alle solo il profilo di Windows Phone. un progetto destinato alla versione completa di Silverlight 4.0 Framework non vede il SDK in Gestione riferimenti.  
  
5.  MinVSVersion: versione minima di Visual Studio.  
  
6.  MaxPlatformVerson: Versione piattaforma di destinazione massima deve essere consente di specificare le versioni di piattaforma in cui il SDK di estensione non funzionerà. Ad esempio, di Microsoft Visual C++ Runtime Package v11.0 deve fare riferimento solo progetti Windows 8. Pertanto, MaxPlatformVersion del progetto Windows 8 è 8.0. Ciò significa che la gestione di riferimenti vengono esclusi Microsoft Visual C++ Runtime Package per un progetto Windows 8.1 e MSBuild genera un errore quando un [!INCLUDE[win81](../includes/win81-md.md)] progetto fa riferimento a essa. Nota: questo elemento è supportato a partire da [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7.  AppliesTo: specifica gli SDK che sono disponibili in Gestione riferimenti, specificando i tipi di progetto di Visual Studio applicabili. Nove valori vengono riconosciuti: WindowsAppContainer, schermata di VisualC, VB, CSharp, WindowsXAML, JavaScript, gestito e nativo. Può usare l'autore SDK e ("+'), o ("&#124;"), non ("! ") operatori per specificare esattamente l'ambito dei tipi di progetto che si applicano al SDK.  
  
     WindowsAppContainer identifica i progetti per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app.  
  
8.  SupportPrefer32Bit: I valori supportati sono "True" e "False". Il valore predefinito è "True". Se il valore è impostato su "False", MSBuild restituisce un errore per [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] progetti (o un avviso per i progetti desktop) se il progetto che fa riferimento al SDK ha Prefer32Bit abilitata. Per altre informazioni sulle Prefer32Bit, vedere [pagina compilazione, creazione progetti (c#)](../ide/reference/build-page-project-designer-csharp.md) oppure [pagina compilazione, creazione progetti (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: elenco delle architetture supportate da SDK delimitato da punti e virgola. MSBuild viene visualizzato un avviso se non è supportata l'architettura di destinazione SDK nel progetto utilizzato. Se questo attributo non è specificato, MSBuild non visualizza mai questo tipo di avviso.  
  
10. SupportsMultipleVersions: se questo attributo è impostato su **errore** oppure **avviso**, MSBuild indica che lo stesso progetto non è possibile fare riferimento a più versioni della stessa famiglia SDK. Se questo attributo non esiste o è impostato su **Consenti**, MSBuild non visualizzare questo tipo di errore o avviso.  
  
11. AppX: Specifica il percorso per i pacchetti di app per la libreria di componenti di Windows sul disco. Questo valore viene passato al componente di registrazione della libreria di componenti di Windows durante il debug locale. La convenzione di denominazione per il nome del file viene  **\<aziendale >.\< Product >. \<Architettura >. \<Configuration >. \<Versione >. AppX**. Configurazione e architettura sono facoltativi nel nome dell'attributo e il valore dell'attributo se non si applicano alla libreria di componenti di Windows. Questo valore è applicabile solo per le librerie dei componenti di Windows.  
  
12. CopyRedistToSubDirectory: specifica dove copiare i file nella cartella \redist relativo alla radice del pacchetto dell'app (vale a dire il **posizione pacchetto** scelto nella procedura guidata Crea pacchetto dell'App) e runtime layout radice. Il percorso predefinito è la radice del pacchetto di app e del layout di F5.  
  
13. DependsOn: Un elenco di identità SDK che definiscono gli SDK da cui dipende questo SDK. Questo attributo viene visualizzato nel riquadro dei dettagli di gestione riferimenti.  
  
14. MoreInfo: l'URL alla pagina web che fornisce la Guida e altre informazioni. Questo valore viene utilizzato nel collegamento per altre informazioni nel riquadro destro di gestione riferimenti.  
  
15. Tipo di registrazione: specifica la registrazione WinMD nel manifesto dell'app ed è obbligatorio per WinMD nativi, che ha un'implementazione controparte DLL.  
  
16. Riferimento al file: specificare per solo tali riferimenti contengono controlli o i file Winmd nativo. Per informazioni su come specificare se un riferimento contiene i controlli, vedere [che specifica la posizione di elementi della casella degli strumenti](#ToolboxItems) sotto.  
  
##  <a name="ToolboxItems"></a> Specifica la posizione degli elementi della casella degli strumenti  
 L'elemento ToolBoxItems dello schema di Sdkmanifest specifica la categoria e la posizione degli elementi della casella degli strumenti in piattaforma e gli SDK di estensione. Negli esempi seguenti viene illustrato come specificare percorsi diversi. Questo è applicabile ai riferimenti WinMD o DLL.  
  
1.  Inserire i controlli nella categoria della casella degli strumenti predefinita.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Inserire i controlli in un determinato nome di categoria.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Inserire i controlli associati a nomi di categoria specifica.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Inserire i controlli associati a nomi di categoria diversa in Blend e Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Enumerare i controlli specifici in modo diverso in Blend e Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerare specifici controlli e inserirli in un percorso comune Visual Studio o solo nel gruppo di tutti i controlli.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Enumerare i controlli specifici e visualizzare solo un set specifico nel ChooseItems senza di essi si trovino nella casella degli strumenti.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procedura dettagliata: Creazione di un SDK tramite C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)
