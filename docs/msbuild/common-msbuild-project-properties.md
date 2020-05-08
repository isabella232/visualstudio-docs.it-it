---
title: Proprietà di progetto MSBuild comuni | Microsoft Docs
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece57a102851efe0198f8993b60dba8e0eae6dec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634422"
---
# <a name="common-msbuild-project-properties"></a>Proprietà di progetto MSBuild comuni

Nella tabella seguente sono elencate le proprietà usate di frequente definite nei file di progetto di Visual Studio o incluse nei file con estensione *targets* compresi con MSBuild.

 I file di progetto in Visual Studio (con estensione *csproj*, *vbproj*, *vcxproj* e altre) contengono il codice XML di MSBuild che viene eseguito quando si compila un progetto usando l'IDE. I progetti importano generalmente uno o più file con estensione *targets* per definire il processo di compilazione. Per altre informazioni, vedere [File con estensione targets di MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Elenco delle proprietà e dei parametri comuni

| Nome della proprietà o del parametro | Description |
|------------------------------------| - |
| AdditionalLibPaths | Specifica le cartelle aggiuntive nelle quali i compilatori devono cercare gli assembly di riferimento. |
| AddModules | Fa sì che il compilatore renda disponibili per il progetto in compilazione tutte le informazioni sui tipi presenti nei file specificati. Questa proprietà è equivalente all'opzione del compilatore `/addModules`. |
| ALToolPath | Percorso in cui si trova *AL.exe*. Questa proprietà esegue l'override della versione corrente di *AL.exe* per consentire l'uso di una versione diversa. |
| ApplicationIcon | File di icona (con estensione *ico*) da passare al compilatore per l'incorporamento come icona Win32. La proprietà è equivalente all'opzione del compilatore `/win32icon`. |
| ApplicationManifest | Specifica il percorso del file usato per generare le informazioni del manifesto esterno del controllo dell'account utente. Si applica solo ai progetti Visual Studio destinati a Windows Vista.<br /><br /> Nella maggior parte dei casi, il manifesto è incorporato. Tuttavia, se si usa la distribuzione COM o ClickOnce senza registrazione, il manifesto può essere un file esterno installato insieme agli assembly dell'applicazione. Per altre informazioni, vedere la proprietà NoWin32Manifest descritta in questo argomento. |
| AssemblyOriginatorKeyFile | Specifica il file usato per firmare l'assembly (con estensione *snk* o *pfx*) e passato all'[attività ResolveKeySource](../msbuild/resolvekeysource-task.md) per generare la chiave effettiva usata per firmare l'assembly. |
| AssemblySearchPaths | Elenco di percorsi da usare per la ricerca durante la risoluzione degli assembly di riferimento in fase di compilazione. L'ordine dei percorsi nell'elenco è significativo perché i percorsi elencati prima hanno la precedenza sulle voci successive. |
| AssemblyName | Nome dell'assembly di output finale dopo la compilazione del progetto. |
| BaseAddress | Specifica l'indirizzo di base dell'assembly di output principale. Questa proprietà è equivalente all'opzione del compilatore `/baseaddress`. |
| BaseIntermediateOutputPath | Cartella di primo livello dove vengono create tutte le cartelle di output intermedie specifiche della configurazione. Il valore predefinito è `obj\`. Di seguito è riportato un esempio di codice: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Specifica il percorso di base del file di output. Se è impostato, MSBuild utilizzerà `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Esempio di sintassi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Valore booleano che indica se i riferimenti al progetto vengono compilati o puliti in parallelo quando viene utilizzata la funzione MSBuild multiproc. Il valore predefinito è `true`, in base al quale i progetti saranno compilati in parallelo se il sistema ha più core o processori. |
| BuildProjectReferences | Valore booleano che indica se i riferimenti al progetto sono compilati da MSBuild. Impostare automaticamente su `false` se si compila il progetto in Visual Studio Integrated Development Environment (IDE), `true` in caso contrario. È possibile specificare `-p:BuildProjectReferences=false` nella riga di comando per evitare di controllare che i progetti di riferimento siano aggiornati. |
| CleanFile | Nome del file che verrà usato come "cache pulita". Per "cache pulita" si intende un elenco di file generati da eliminare durante l'operazione di pulizia. Il file è inserito nel percorso di output intermedio dal processo di compilazione.<br /><br /> Questa proprietà specifica solo i nomi di file privi delle informazioni sul percorso. |
| CodePage | Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Questa proprietà è equivalente all'opzione del compilatore `/codepage`. |
| CompilerResponseFile | File di risposta facoltativo che può essere passato alle attività del compilatore. |
| Configurazione | Configurazione in corso di compilazione, "debug" o "rilascio". |
| CscToolPath | Il percorso di *csc. exe*, il compilatore C#. |
| CustomBeforeMicrosoftCommonTargets | Nome di un file di progetto o file delle destinazioni che deve essere importato automaticamente prima dell'importazione delle destinazioni comuni. |
| DebugSymbols | Valore booleano che indica se i simboli sono generati dalla compilazione.<br /><br /> Impostando **-p:DebugSymbols = false** nella riga di comando viene disabilitata la generazione di file di simboli del database di programma (con*estensione PDB*). |
| DebugType | Definisce il livello di informazioni di debug da generare. I valori validi sono "full," "pdbonly," "portable", "embedded" e "none." |
| DefineConstants | Definisce le costanti del compilatore condizionali. Le coppie simbolo/valore sono separate da punti e virgola e vengono specificate mediante la seguente sintassi:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> La proprietà è equivalente all'opzione del compilatore `/define`. |
| DefineDebug | Valore booleano che indica se la costante DEBUG deve essere definita. |
| DefineTrace | Valore booleano che indica se la costante TRACE deve essere definita. |
| DelaySign | Valore booleano che indica se apporre una firma ritardata all'assembly anziché quella completa. |
| Deterministico | Un valore booleano che indica se il compilatore deve produrre assembly identici per input identici. Questo parametro corrisponde all'opzione `/deterministic` dei compilatori *vbc.exe* e *csc.exe*. |
| DisabledWarnings | Non visualizza gli avvisi specificati. È necessario specificare solo la parte numerica dell'identificatore di avviso. Se si specificano più avvisi, usare il punto e virgola per separarli. Questo parametro corrisponde all'opzione `/nowarn` del compilatore *vbc.exe*. |
| DisableFastUpToDateCheck | Valore booleano che si applica solo a Visual Studio. Il gestore di compilazione di Visual Studio usa un processo denominato FastUpToDateCheck per determinare se un progetto deve essere ricompilato per essere aggiornato. Questo processo è più veloce rispetto all'utilizzo di MSBuild per determinare questo problema. Impostando la proprietà della DisableFastUpToDateCheck `true` su è possibile ignorare il gestore della compilazione di Visual Studio e forzarlo a usare MSBuild per determinare se il progetto è aggiornato. |
| DocumentationFile | Nome del file generato come file di documentazione XML. Include solo il nome di file senza informazioni sul percorso. |
| ErrorReport | Specifica la modalità di segnalazione degli errori interni del compilatore. I valori validi sono "prompt", "send" o "none". Questa proprietà è equivalente all'opzione del compilatore `/errorreport`. |
| ExcludeDeploymentUrl | L'[attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)aggiunge un tag deploymentProvider al manifesto della distribuzione se il file di progetto contiene uno degli elementi seguenti:<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> Se si utilizza ExcludeDeploymentUrl, tuttavia, è possibile evitare che il tag deploymentProvider venga aggiunto al manifesto di distribuzione anche se viene specificato uno degli URL riportati sopra. A tale scopo, aggiungere la proprietà seguente al file di progetto:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Nota:**  ExcludeDeploymentUrl non è esposto nell'IDE di Visual Studio e può essere impostato solo modificando manualmente il file di progetto. L'impostazione di questa proprietà non influisce sulla pubblicazione in Visual Studio. ovvero, il tag deploymentProvider verrà comunque aggiunto all'URL specificato da PublishUrl. |
| FileAlignment | Specifica, in byte, il punto in cui allineare le sezioni del file di output. I valori validi sono 512, 1024, 2048, 4096, 8192. Questa proprietà è equivalente all'opzione del compilatore `/filealignment`. |
| FrameworkPathOverride | Specifica il percorso dei file *mscorlib. dll* e *Microsoft. VisualBasic. dll*. Questo parametro è equivalente all'opzione `/sdkpath` del compilatore *vbc.exe*. |
| GenerateDocumentation | (C#, Visual Basic) Parametro booleano che indica se la documentazione è generata dalla compilazione. Se `true`, la compilazione genera informazioni sulla documentazione e le inserisce in un file con *estensione XML* insieme al nome del file eseguibile o della libreria creata dall'attività di compilazione. |
| GenerateFullPaths | C# Generare percorsi completi per i nomi di file nell'output usando l'opzione del compilatore [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | Indica se gli assembly di serializzazione XML devono essere generati da *SGen.exe*, che può essere impostato su attivato, automatico o disattivato. Questa proprietà viene utilizzata solo per gli assembly la cui destinazione è .NET Framework. Per generare assembly di serializzazione XML per gli assembly di .NET Standard o .NET Core, fare riferimento al pacchetto NuGet *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Percorso di output intermedio completo derivato da `BaseIntermediateOutputPath`, se non viene specificato alcun percorso. Ad esempio *\obj\debug\\*. |
| KeyContainerName | Nome del contenitore di chiavi con nome sicuro. |
| KeyOriginatorFile | Nome del file di chiave con nome sicuro. |
| ModuleAssemblyName | Nome dell'assembly nel quale il modulo compilato deve essere incorporato. La proprietà è equivalente all'opzione del compilatore `/moduleassemblyname`. |
| MSBuildProjectExtensionsPath | Specifica il percorso in cui si trovano le estensioni di progetto. Per impostazione predefinita, assume lo stesso valore di `BaseIntermediateOutputPath`. |
| NoLogo | Valore booleano che indica se si desidera disattivare il logo del compilatore. Questa proprietà è equivalente all'opzione del compilatore `/nologo`. |
| NoStdLib | Valore booleano che indica se evitare il riferimento alla libreria standard (*mscorlib.dll*). Il valore predefinito è `false`. |
| NoVBRuntimeReference | Valore booleano che indica se il runtime di Visual Basic (*Microsoft. VisualBasic. dll*) deve essere incluso come riferimento nel progetto. |
| NoWin32Manifest | Valore booleano che indica se le informazioni sul manifesto del controllo dell'account utente verranno incorporate nel file eseguibile dell'applicazione. Si applica solo ai progetti Visual Studio destinati a Windows Vista. Nei progetti distribuiti tramite ClickOnce e COM senza registrazione, questo elemento viene ignorato. `False` (valore predefinito) specifica che le informazioni sul manifesto del controllo dell'account utente verranno incorporate nel file eseguibile dell'applicazione. `True` specifica che le informazioni sul manifesto del controllo dell'account utente non verranno incorporate.<br /><br /> Questa proprietà si applica solo ai progetti Visual Studio destinati a Windows Vista. Nei progetti distribuiti tramite ClickOnce e COM senza registrazione, questa proprietà viene ignorata.<br /><br /> È necessario aggiungere NoWin32Manifest solo se non si vuole che in Visual Studio vengano incorporate informazioni sul manifesto nell'eseguibile dell'applicazione; Questo processo è denominato *virtualizzazione*. Per usare la virtualizzazione, impostare `<ApplicationManifest>` insieme a `<NoWin32Manifest>` nel modo seguente:<br /><br /> -Per i progetti di Visual Basic, `<ApplicationManifest>` rimuovere il nodo. (In Visual Basic progetti, `<NoWin32Manifest>` viene ignorato quando esiste `<ApplicationManifest>` un nodo).<br />-Per i progetti C#, `<ApplicationManifest>` impostare `False` su `<NoWin32Manifest>` e `True`su. Nei progetti C# `<ApplicationManifest>` esegue l'override `<NoWin32Manifest>`di.<br /> Questa proprietà è equivalente all'opzione `/nowin32manifest` del compilatore di *vbc. exe*. |
| Ottimizzazione | Valore booleano che, se impostato su `true`, abilita le ottimizzazioni del compilatore. Questa proprietà è equivalente all'opzione del compilatore `/optimize`. |
| OptionCompare | Specifica la modalità con cui vengono confrontate le stringhe. I valori validi sono "binary" o "text". Questa proprietà è equivalente all'opzione `/optioncompare` del compilatore di *vbc. exe*. |
| OptionExplicit | Valore booleano che, se impostato su `true`, richiede la dichiarazione esplicita delle variabili nel codice sorgente. Questa proprietà è equivalente all'opzione del compilatore `/optionexplicit`. |
| OptionInfer | Valore booleano che, se impostato su `true`, abilita l'inferenza dei tipi delle variabili. Questa proprietà è equivalente all'opzione del compilatore `/optioninfer`. |
| OptionStrict | Valore booleano che, se impostato su `true`, fa sì che l'attività di compilazione applichi la semantica dei tipi rigida per limitare le conversioni dei tipi impliciti. Questa proprietà è equivalente all'opzione `/optionstrict` del compilatore *vbc.exe*. |
| OutDir | Indica il percorso di output finale per il progetto o la soluzione. Quando si compila una soluzione, è possibile usare OutDir per raccogliere più output di progetto in un'unica posizione. Inoltre, OutDir è incluso in AssemblySearchPaths usato per la risoluzione dei riferimenti. Ad esempio, *bin\Debug*. |
| Percorso output | Specifica il percorso della directory di output, relativo alla directory del progetto, ad esempio *bin\Debug*. |
| OutputType | Specifica il formato del file di output. Per il parametro è possibile specificare uno dei valori riportati di seguito:<br /><br /> -   Libreria. Crea una libreria di codici. È il valore predefinito.<br />-   Exe. Crea un'applicazione console.<br />-   Modulo. Crea un modulo.<br />-   Winexe. Crea un programma per Windows.<br /><br /> Questa proprietà è equivalente all'opzione `/target` del compilatore *vbc.exe*. |
| OverwriteReadOnlyFiles | Valore booleano che indica se si desidera configurare la compilazione per sovrascrivere i file di sola lettura o attivare un errore. |
| PathMap | Specifica come eseguire il mapping di percorsi fisici ai nomi di percorso di origine restituiti dal compilatore. Questa proprietà è equivalente all'opzione `/pathmap` del compilatore *csc.exe*. |
| PdbFile | Nome del file con estensione *pdp* che si sta generando. Questa proprietà è equivalente all'opzione `/pdb` del compilatore *csc.exe*. |
| Piattaforma | Sistema operativo a cui è destinata la compilazione. I valori validi sono "Any CPU", "x86" e "x64". |
| ProcessorArchitecture | Architettura del processore usata quando vengono risolti i riferimenti all'assembly. I valori validi sono "msil", "x86", "amd64" o "ia64". |
| ProduceOnlyReferenceAssembly | Valore booleano che indica al compilatore di generare solo un assembly di riferimento piuttosto che codice compilato. Non può essere usato in combinazione con `ProduceReferenceAssembly`.  Questa proprietà corrisponde all'opzione `/refonly` dei compilatori *vbc.exe* e *csc.exe*. |
| ProduceReferenceAssembly | Un valore booleano che, se impostato su `true`, consente la produzione di [assembly di riferimento](/dotnet/standard/assembly/reference-assemblies) per l'assembly corrente. `Deterministic` deve essere `true` quando si usa questa funzionalità. Questa proprietà corrisponde all'opzione `/refout` dei compilatori *vbc.exe* e *csc.exe*. |
| RemoveIntegerChecks | Valore booleano che indica se disabilitare i controlli degli errori di overflow di intero. Il valore predefinito è `false`. Questa proprietà è equivalente all'opzione `/removeintchecks` del compilatore *vbc.exe*. |
| RootNamespace | Spazio dei nomi radice da usare quando si assegna un nome a una risorsa incorporata. Questo spazio dei nomi fa parte del nome del manifesto della risorsa incorporata. |
| Satellite_AlgorithmId | ID dell'algoritmo hash *AL.exe* da usare quando si creano assembly satellite. |
| Satellite_BaseAddress | Indirizzo di base da usare quando gli assembly satellite specifici delle impostazioni cultura vengono compilati usando la destinazione `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | Nome dell'azienda da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_Configuration | Nome della configurazione da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_Description | Testo della descrizione da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_EvidenceFile | Incorpora il file specificato nell'assembly satellite con il nome di risorsa "Security.Evidence". |
| Satellite_FileVersion | Specifica una stringa per il campo relativo alla versione del file nell'assembly satellite. |
| Satellite_Flags | Specifica un valore per il campo relativo ai flag dell'assembly satellite. |
| Satellite_GenerateFullPaths | Determina l'utilizzo di percorsi assoluti durante la compilazione per qualsiasi file segnalato in un messaggio di errore. |
| Satellite_LinkResource | Collega i file di risorse specificati a un assembly satellite. |
| Satellite_MainEntryPoint | Specifica il nome completo, ovvero classe.metodo, del metodo da usare come punto di ingresso quando un modulo viene convertito in un file eseguibile durante la generazione dell'assembly satellite. |
| Satellite_ProductName | Specifica una stringa per il campo relativo al nome del prodotto dell'assembly satellite. |
| Satellite_ProductVersion | Specifica una stringa per il campo relativo alla versione del prodotto nell'assembly satellite. |
| Satellite_TargetType | Specifica il formato del file di output dell'assembly satellite, come "library", "exe" o "win". Il valore predefinito è "library". |
| Satellite_Title | Specifica una stringa per il campo relativo al titolo dell'assembly satellite. |
| Satellite_Trademark | Specifica una stringa per il campo relativo al marchio dell'assembly satellite. |
| Satellite_Version | Specifica le informazioni sulla versione dell'assembly satellite. |
| Satellite_Win32Icon | Inserisce un file di icona estensione *ico* nell'assembly satellite. |
| Satellite_Win32Resource | Inserisce una risorsa Win32 (file con estensione *res*) nell'assembly satellite. |
| SGenToolPath | Percorso dello strumento facoltativo che indica da dove ottenere *SGen.exe* quando viene eseguito l'override della versione corrente di *SGen.exe*. Questa proprietà viene usata solo per .NET Framework.|
| SGenUseProxyTypes | Valore booleano che indica se i tipi proxy devono essere generati da *SGen.exe*. Si applica solo quando *GenerateSerializationAssemblies* è attivato e solo per .NET Framework.<br /><br /> La destinazione SGen usa questa proprietà per impostare il flag UseProxyTypes. L'impostazione predefinita di questa proprietà è true e tale valore non può essere modificato dall'interfaccia utente. Per generare l'assembly di serializzazione per tipi non WebService, aggiungere questa proprietà al file di progetto e impostarla su False prima di importare *Microsoft.Common.Targets* o *C#/VB.targets*. |
| StartupObject | Specifica la classe o il modulo che contiene il metodo Main o la procedura Sub Main. Questa proprietà è equivalente all'opzione del compilatore `/main`. |
| SubsystemVersion | Specifica la versione minima del sottosistema che può essere usata dal file eseguibile generato. Questa proprietà è equivalente all'opzione del compilatore `/subsystemversion`. Per informazioni sul valore predefinito di questa proprietà, vedere [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) o [/subsystemversion (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Versione di .NET Compact Framework richiesta per eseguire l'applicazione in corso di compilazione. Se si imposta questa proprietà, è possibile fare riferimento a determinati assembly del framework a cui non è possibile fare riferimento in altro modo. |
| TargetFrameworkVersion | Versione di .NET Framework richiesta per eseguire l'applicazione in corso di compilazione. Se si imposta questa proprietà, è possibile fare riferimento a determinati assembly del framework a cui non è possibile fare riferimento in altro modo. |
| TreatWarningsAsErrors | Parametro booleano che, se impostato su `true`, fa sì che tutti gli avvisi vengano considerati errori. Questo parametro è equivalente all'opzione del compilatore `/nowarn`. |
| UseHostCompilerIfAvailable | Parametro booleano che, se impostato su `true`, fa sì che l'attività di compilazione utilizzi l'oggetto del compilatore in-process, se disponibile. Questo parametro viene usato solo da Visual Studio. |
| Utf8Output | Parametro booleano che, se impostato su `true`, registra l'output del compilatore usando la codifica UTF-8. Questo parametro è equivalente all'opzione del compilatore `/utf8Output`. |
| VbcToolPath | Percorso facoltativo che indica un altro percorso di *vbc.exe* quando viene eseguito l'override della versione corrente di *vbc.exe*. |
| VbcVerbosity | Specifica il livello di dettaglio dell'output del compilatore Visual Basic. I valori validi sono "Non interattivo", "Normale" (valore predefinito) o "Dettagliato". |
| VisualStudioVersion | Specifica in quale versione di Visual Studio deve essere considerato in esecuzione questo progetto. Se non si specifica questa proprietà, MSBuild la imposta su un valore predefinito appropriato.<br /><br /> Questa proprietà viene usata in diversi tipi di progetto per specificare il set di destinazioni usate per la compilazione. Se `ToolsVersion` è impostato su 4.0 o un valore superiore per un progetto, la proprietà `VisualStudioVersion` viene usata per specificare quale set di strumenti secondario usare. Per altre informazioni, vedere [Set di strumenti MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Specifica un elenco di avvisi da considerare come errori. Questo parametro è equivalente all'opzione del compilatore `/warnaserror`. |
| WarningsNotAsErrors | Specifica un elenco di avvisi che non vengono considerati errori. Questo parametro è equivalente all'opzione del compilatore `/warnaserror`. |
| Win32Manifest | Nome del file manifesto che deve essere incorporato nell'assembly finale. Questo parametro è equivalente all'opzione del compilatore `/win32Manifest`. |
| Win32Resource | Nome file della risorsa Win32 da incorporare nell'assembly finale. Questo parametro è equivalente all'opzione del compilatore `/win32resource`. |

## <a name="see-also"></a>Vedere anche

- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
