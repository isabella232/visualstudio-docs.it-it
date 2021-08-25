---
title: Proprietà di progetto MSBuild comuni | Microsoft Docs
description: Informazioni sulle MSBuild di progetto comuni che possono essere definite o usate nei file di progetto o incluse nei file con estensione targets MSBuild disponibili.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 55d2ecda1619f187f1a1fdd0854eb1e3dd1d7fb8
ms.sourcegitcommit: 92cfc4b09f2f1847fb3af72521e304af9a3c35b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122765476"
---
# <a name="common-msbuild-project-properties"></a>Proprietà di progetto MSBuild comuni

Nella tabella seguente sono elencate le proprietà usate di frequente definite nei file di progetto di Visual Studio o incluse nei file con estensione *targets* compresi con MSBuild.

 I file di progetto in Visual Studio (con estensione *csproj*, *vbproj*, *vcxproj* e altre) contengono il codice XML di MSBuild che viene eseguito quando si compila un progetto usando l'IDE. I progetti importano generalmente uno o più file con estensione *targets* per definire il processo di compilazione. Per altre informazioni, vedere [File con estensione targets di MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Elenco delle proprietà e dei parametri comuni

| Nome della proprietà o del parametro | Tipi di progetto | Descrizione |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Specifica le cartelle aggiuntive nelle quali i compilatori devono cercare gli assembly di riferimento. |
| AddModules | .NET | Fa sì che il compilatore renda disponibili per il progetto in compilazione tutte le informazioni sui tipi presenti nei file specificati. Questa proprietà è equivalente all'opzione del compilatore `/addModules`. |
| ALToolPath | .NET | Percorso in cui si trova *AL.exe*. Questa proprietà esegue l'override della versione corrente di *AL.exe* per consentire l'uso di una versione diversa. |
| ApplicationIcon | .NET | File di icona (con estensione *ico*) da passare al compilatore per l'incorporamento come icona Win32. La proprietà è equivalente all'opzione del compilatore `/win32icon`. |
| ApplicationManifest | Tutti | Specifica il percorso del file usato per generare le informazioni del manifesto esterno del controllo dell'account utente. Si applica solo ai Visual Studio di destinazione Windows Vista.<br /><br /> Nella maggior parte dei casi, il manifesto è incorporato. Tuttavia, se si usa registration free COM o ClickOnce distribuzione, il manifesto può essere un file esterno che viene installato insieme agli assembly dell'applicazione. Per altre informazioni, vedere la proprietà NoWin32Manifest descritta in questo argomento. |
| AssemblyOriginatorKeyFile | .NET | Specifica il file usato per firmare l'assembly (con estensione *snk* o *pfx*) e passato all'[attività ResolveKeySource](../msbuild/resolvekeysource-task.md) per generare la chiave effettiva usata per firmare l'assembly. |
| AssemblySearchPaths | .NET | Elenco di percorsi da usare per la ricerca durante la risoluzione degli assembly di riferimento in fase di compilazione. L'ordine dei percorsi nell'elenco è significativo perché i percorsi elencati prima hanno la precedenza sulle voci successive. |
| AssemblyName | .NET | Nome dell'assembly di output finale dopo la compilazione del progetto. |
| BaseAddress | .NET | Specifica l'indirizzo di base dell'assembly di output principale. Questa proprietà è equivalente all'opzione del compilatore `/baseaddress`. |
| BaseIntermediateOutputPath | Tutti | Cartella di primo livello dove vengono create tutte le cartelle di output intermedie specifiche della configurazione. Il valore predefinito è `obj\`. Di seguito è riportato un esempio di codice: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Tutti | Specifica il percorso di base del file di output. Se è impostata, MSBuild userà `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Esempio di sintassi: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Tutti | Valore booleano che indica se i riferimenti al progetto vengono compilati o puliti in parallelo quando MSBuild multi-proc. Il valore predefinito è `true`, in base al quale i progetti saranno compilati in parallelo se il sistema ha più core o processori. |
| BuildProjectReferences | Tutti | Valore booleano che indica se i riferimenti al progetto vengono compilati MSBuild. Impostare automaticamente su se si compila il progetto nell'ambiente Visual Studio di sviluppo `false` integrato (IDE), `true` in caso contrario. È possibile specificare `-p:BuildProjectReferences=false` nella riga di comando per evitare di controllare che i progetti di riferimento siano aggiornati. |
| CleanFile | Tutti | Nome del file che verrà usato come "cache pulita". Per "cache pulita" si intende un elenco di file generati da eliminare durante l'operazione di pulizia. Il file è inserito nel percorso di output intermedio dal processo di compilazione.<br /><br /> Questa proprietà specifica solo i nomi di file privi delle informazioni sul percorso. |
| CodePage | .NET | Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Questa proprietà è equivalente all'opzione del compilatore `/codepage`. |
| CompilerResponseFile | .NET | File di risposta facoltativo che può essere passato alle attività del compilatore. |
| Configurazione | Tutti | Configurazione che si sta compilando, in genere `Debug` o `Release` , ma configurabile a livello di soluzione e di progetto. |
| CscToolPath | C# | Percorso di *csc.exe*, il compilatore C#. |
| CustomBeforeMicrosoftCommonTargets | Tutti | Nome di un file di progetto o file delle destinazioni che deve essere importato automaticamente prima dell'importazione delle destinazioni comuni. |
| DebugSymbols | Tutti | Valore booleano che indica se i simboli sono generati dalla compilazione.<br /><br /> **L'impostazione -p:DebugSymbols=false** nella riga di comando disabilita la generazione di file di simboli del database di programma (*con estensione pdb).* |
| DebugType | Tutti | Definisce il livello di informazioni di debug da generare. I valori validi sono "full," "pdbonly," "portable", "embedded" e "none." |
| DefineConstants | .NET | Definisce le costanti del compilatore condizionali. Le coppie simbolo/valore sono separate da punti e virgola e vengono specificate mediante la seguente sintassi:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> La proprietà è equivalente all'opzione del compilatore `/define`. |
| DefineDebug | Tutti |  Valore booleano che indica se la costante DEBUG deve essere definita. |
| DefineTrace | Tutti | Valore booleano che indica se la costante TRACE deve essere definita. |
| DelaySign | .NET | Valore booleano che indica se apporre una firma ritardata all'assembly anziché quella completa. |
| Deterministico | .NET | Un valore booleano che indica se il compilatore deve produrre assembly identici per input identici. Questo parametro corrisponde `/deterministic` all'opzione dei compilatori. |
| DisableFastUpToDateCheck | Tutti | Valore booleano che si applica solo Visual Studio. Il Visual Studio compilazione usa un processo denominato FastUpToDateCheck per determinare se un progetto deve essere ricompilato per essere aggiornato. Questo processo è più veloce rispetto all'MSBuild per determinare questo problema. L'impostazione della proprietà DisableFastUpToDateCheck su consente di ignorare lo strumento di gestione della compilazione Visual Studio e forzarlo a usare MSBuild per determinare se il progetto è `true` aggiornato. |
| DocumentationFile | .NET | Nome del file generato come file di documentazione XML. Include solo il nome di file senza informazioni sul percorso. |
| ErrorReport | .NET | Specifica la modalità di segnalazione degli errori interni del compilatore. I valori validi sono "prompt", "send" o "none". Questa proprietà è equivalente all'opzione del compilatore `/errorreport`. |
| ExcludeDeploymentUrl | .NET | L'[attività GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)aggiunge un tag deploymentProvider al manifesto della distribuzione se il file di progetto contiene uno degli elementi seguenti:<br /><br /> -   UpdateUrl<br />-   InstallUrl<br />-   PublishUrl<br /><br /> Se si utilizza ExcludeDeploymentUrl, tuttavia, è possibile evitare che il tag deploymentProvider venga aggiunto al manifesto di distribuzione anche se viene specificato uno degli URL riportati sopra. A tale scopo, aggiungere la proprietà seguente al file di progetto:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Nota:**  ExcludeDeploymentUrl non viene esposto nell'IDE Visual Studio e può essere impostato solo modificando manualmente il file di progetto. L'impostazione di questa proprietà non influisce sulla pubblicazione all'interno Visual Studio; il tag deploymentProvider verrà comunque aggiunto all'URL specificato da PublishUrl. |
| FileAlignment | .NET | Specifica, in byte, il punto in cui allineare le sezioni del file di output. I valori validi sono 512, 1024, 2048, 4096, 8192. Questa proprietà è equivalente all'opzione del compilatore `/filealignment`. |
| FrameworkPathOverride | Visual Basic | Specifica la posizione dei *mscorlib.dll* e *microsoft.visualbasic.dll*. Questo parametro è equivalente all'opzione `/sdkpath` del compilatore *vbc.exe*. |
| GenerateDocumentation | .NET | Parametro booleano che indica se la documentazione è generata dalla compilazione. Se , la compilazione genera informazioni sulla documentazione e le inserisce in un file.xmlinsieme al nome del file eseguibile o della libreria `true` creata dall'attività  di compilazione. |
| GenerateFullPaths | C# | Generare percorsi completi per i nomi file nell'output usando [l'opzione del compilatore -fullpaths.](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) |
| GenerateSerializationAssemblies | .NET | Indica se gli assembly di serializzazione XML devono essere generati da *SGen.exe*, che può essere impostato su attivato, automatico o disattivato. Questa proprietà viene utilizzata solo per gli assembly la cui destinazione è .NET Framework. Per generare assembly di serializzazione XML per gli assembly di .NET Standard o .NET Core, fare riferimento al pacchetto NuGet *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Tutti | Percorso di output intermedio completo derivato da `BaseIntermediateOutputPath`, se non viene specificato alcun percorso. Ad esempio, *obj\debug \\*. |
| KeyContainerName | Tutti | Nome del contenitore di chiavi con nome sicuro. |
| KeyOriginatorFile | Tutti | Nome del file di chiave con nome sicuro. |
| ModuleAssemblyName | .NET | Nome dell'assembly nel quale il modulo compilato deve essere incorporato. La proprietà è equivalente all'opzione del compilatore `/moduleassemblyname`. |
| MSBuildProjectExtensionsPath | Tutti | Specifica il percorso in cui si trovano le estensioni di progetto. Per impostazione predefinita, assume lo stesso valore di `BaseIntermediateOutputPath`. |
| NoLogo | Tutti | Valore booleano che indica se si desidera disattivare il logo del compilatore. Questa proprietà è equivalente all'opzione del compilatore `/nologo`. |
| NoStdLib | .NET | Valore booleano che indica se evitare il riferimento alla libreria standard (*mscorlib.dll*). Il valore predefinito è `false`. |
| NoVBRuntimeReference | Visual Basic | Valore booleano che indica se il runtime Visual Basic (*Microsoft.VisualBasic.dll*) deve essere incluso come riferimento nel progetto. |
| NoWarn | .NET | Non visualizza gli avvisi specificati. È necessario specificare solo la parte numerica dell'identificatore di avviso. Se si specificano più avvisi, usare il punto e virgola per separarli. Questo parametro corrisponde `/nowarn` all'opzione dei compilatori. |
| NoWin32Manifest | .NET | Valore booleano che indica se le informazioni sul manifesto del controllo dell'account utente verranno incorporate nel file eseguibile dell'applicazione. Si applica solo Visual Studio progetti di destinazione Windows Vista. Nei progetti distribuiti usando ClickOnce e Registration-Free COM, questo elemento viene ignorato. `False` (valore predefinito) specifica che le informazioni sul manifesto del controllo dell'account utente verranno incorporate nel file eseguibile dell'applicazione. `True` specifica che le informazioni sul manifesto del controllo dell'account utente non verranno incorporate.<br /><br /> Questa proprietà si applica solo ai Visual Studio di destinazione Windows Vista. Nei progetti distribuiti usando ClickOnce e Registration-Free COM, questa proprietà viene ignorata.<br /><br /> È consigliabile aggiungere NoWin32Manifest solo se non Visual Studio incorporare le informazioni del manifesto nel file eseguibile dell'applicazione. questo processo è denominato *virtualizzazione*. Per usare la virtualizzazione, impostare `<ApplicationManifest>` insieme a `<NoWin32Manifest>` nel modo seguente:<br /><br /> - Per Visual Basic, rimuovere il `<ApplicationManifest>` nodo. Nei progetti Visual Basic, `<NoWin32Manifest>` viene ignorato quando `<ApplicationManifest>` esiste un nodo.<br />- Per i progetti C#, impostare `<ApplicationManifest>` su `False` e su `<NoWin32Manifest>` `True` . Nei progetti C# esegue `<ApplicationManifest>` l'override di `<NoWin32Manifest>` .<br /> Questa proprietà equivale all'opzione `/nowin32manifest` del compilatore di *vbc.exe*. |
| Ottimizzazione | .NET | Valore booleano che, se impostato su `true`, abilita le ottimizzazioni del compilatore. Questa proprietà è equivalente all'opzione del compilatore `/optimize`. |
| OptionCompare | VisualBasic | Specifica la modalità con cui vengono confrontate le stringhe. I valori validi sono "binary" o "text". Questa proprietà equivale all'opzione `/optioncompare` del compilatore di *vbc.exe*. |
| OptionExplicit | Visual Basic | Valore booleano che, se impostato su `true`, richiede la dichiarazione esplicita delle variabili nel codice sorgente. Questa proprietà è equivalente all'opzione del compilatore `/optionexplicit`. |
| OptionInfer | Visual Basic | Valore booleano che, se impostato su `true`, abilita l'inferenza dei tipi delle variabili. Questa proprietà è equivalente all'opzione del compilatore `/optioninfer`. |
| OptionStrict | Visual Basic | Valore booleano che, se impostato su `true`, fa sì che l'attività di compilazione applichi la semantica dei tipi rigida per limitare le conversioni dei tipi impliciti. Questa proprietà è equivalente all'opzione `/optionstrict` del compilatore *vbc.exe*. |
| OutDir | Tutti | Indica il percorso di output finale per il progetto o la soluzione. Quando si compila una soluzione, è possibile usare OutDir per raccogliere più output del progetto in un'unica posizione. Inoltre, OutDir è incluso in AssemblySearchPaths usato per la risoluzione dei riferimenti. Ad esempio, *bin\Debug*. |
| Percorso output | Tutti | Specifica il percorso della directory di output, relativo alla directory del progetto, ad esempio *bin\Debug*. |
| OutputType | Tutti |  Specifica il formato del file di output. Per il parametro è possibile specificare uno dei valori riportati di seguito:<br /><br /> -   Libreria. Crea una libreria di codici. È il valore predefinito.<br />-   Exe. Crea un'applicazione console.<br />-   Modulo. Crea un modulo.<br />-   Winexe. Crea un programma per Windows.<br /><br /> Per C# e Visual Basic, questa proprietà equivale `/target` all'opzione . |
| OverwriteReadOnlyFiles | Tutti | Valore booleano che indica se si desidera configurare la compilazione per sovrascrivere i file di sola lettura o attivare un errore. |
| PathMap | .NET | Specifica come eseguire il mapping di percorsi fisici ai nomi di percorso di origine restituiti dal compilatore. Questa proprietà equivale `/pathmap` all'opzione dei compilatori. |
| PdbFile | .NET | Nome del file con estensione *pdp* che si sta generando. Questa proprietà è equivalente all'opzione `/pdb` del compilatore *csc.exe*. |
| Piattaforma | Tutti | Sistema operativo a cui è destinata la compilazione. Esempi per .NET Framework build sono "Any CPU", "x86" e "x64". |
| ProcessorArchitecture | .NET | Architettura del processore usata quando vengono risolti i riferimenti all'assembly. I valori validi sono "msil", "x86", "amd64" o "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Valore booleano che indica al compilatore di generare solo un assembly di riferimento piuttosto che codice compilato. Non può essere usato in combinazione con `ProduceReferenceAssembly`.  Questa proprietà corrisponde all'opzione `/refonly` dei compilatori *vbc.exe* e *csc.exe*. |
| ProduceReferenceAssembly | .NET | Un valore booleano che, se impostato su `true`, consente la produzione di [assembly di riferimento](/dotnet/standard/assembly/reference-assemblies) per l'assembly corrente. `Deterministic` deve essere `true` quando si usa questa funzionalità. Questa proprietà corrisponde all'opzione `/refout` dei compilatori *vbc.exe* e *csc.exe*. |
| RemoveIntegerChecks | Visual Basic | Valore booleano che indica se disabilitare i controlli degli errori di overflow di intero. Il valore predefinito è `false`. Questa proprietà è equivalente all'opzione `/removeintchecks` del compilatore *vbc.exe*. |
| RootNamespace | Tutti | Spazio dei nomi radice da usare quando si assegna un nome a una risorsa incorporata. Questo spazio dei nomi fa parte del nome del manifesto della risorsa incorporata. |
| Satellite_AlgorithmId | .NET | ID dell'algoritmo hash *AL.exe* da usare quando si creano assembly satellite. |
| Satellite_BaseAddress | .NET | Indirizzo di base da usare quando gli assembly satellite specifici delle impostazioni cultura vengono compilati usando la destinazione `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | .NET | Nome dell'azienda da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_Configuration | .NET | Nome della configurazione da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_Description | .NET | Testo della descrizione da passare ad *AL.exe* durante la generazione degli assembly satellite. |
| Satellite_EvidenceFile | .NET | Incorpora il file specificato nell'assembly satellite con il nome di risorsa "Security.Evidence". |
| Satellite_FileVersion | .NET | Specifica una stringa per il campo relativo alla versione del file nell'assembly satellite. |
| Satellite_Flags | .NET | Specifica un valore per il campo relativo ai flag dell'assembly satellite. |
| Satellite_GenerateFullPaths | .NET | Determina l'utilizzo di percorsi assoluti durante la compilazione per qualsiasi file segnalato in un messaggio di errore. |
| Satellite_LinkResource | .NET | Collega i file di risorse specificati a un assembly satellite. |
| Satellite_MainEntryPoint | .NET | Specifica il nome completo, ovvero classe.metodo, del metodo da usare come punto di ingresso quando un modulo viene convertito in un file eseguibile durante la generazione dell'assembly satellite. |
| Satellite_ProductName | .NET | Specifica una stringa per il campo relativo al nome del prodotto dell'assembly satellite. |
| Satellite_ProductVersion | .NET | Specifica una stringa per il campo relativo alla versione del prodotto nell'assembly satellite. |
| Satellite_TargetType | .NET | Specifica il formato del file di output dell'assembly satellite, come "library", "exe" o "win". Il valore predefinito è "library". |
| Satellite_Title | .NET | Specifica una stringa per il campo relativo al titolo dell'assembly satellite. |
| Satellite_Trademark | .NET | Specifica una stringa per il campo relativo al marchio dell'assembly satellite. |
| Satellite_Version | .NET | Specifica le informazioni sulla versione dell'assembly satellite. |
| Satellite_Win32Icon | .NET | Inserisce un file di icona estensione *ico* nell'assembly satellite. |
| Satellite_Win32Resource | .NET | Inserisce una risorsa Win32 (file con estensione *res*) nell'assembly satellite. |
| SGenToolPath | .NET | Percorso dello strumento facoltativo che indica da dove ottenere *SGen.exe* quando viene eseguito l'override della versione corrente di *SGen.exe*. |
| SGenUseProxyTypes | .NET | Valore booleano che indica se i tipi proxy devono essere generati da *SGen.exe*. Ciò si applica solo quando *GenerateSerializationAssemblies* è impostato su on.<br /><br /> La destinazione SGen usa questa proprietà per impostare il flag UseProxyTypes. L'impostazione predefinita di questa proprietà è true e tale valore non può essere modificato dall'interfaccia utente. Per generare l'assembly di serializzazione per tipi non WebService, aggiungere questa proprietà al file di progetto e impostarla su False prima di importare *Microsoft.Common.Targets* o *C#/VB.targets*. |
| SkipInvalidConfigurations | Tutti | Quando , genera un avviso sulle combinazioni di piattaforma e configurazione non valide, ma non genera errori di compilazione. Quando o non è definito `true` `false` (impostazione predefinita), genera un errore. |
| StartupObject | .NET | Specifica la classe o il modulo che contiene il metodo Main o la procedura Sub Main. Questa proprietà è equivalente all'opzione del compilatore `/main`. |
| SubsystemVersion | .NET | Specifica la versione minima del sottosistema che può essere usata dal file eseguibile generato. Questa proprietà è equivalente all'opzione del compilatore `/subsystemversion`. Per informazioni sul valore predefinito di questa proprietà, vedere [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) o [/subsystemversion (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Versione di .NET Compact Framework richiesta per eseguire l'applicazione in corso di compilazione. Se si imposta questa proprietà, è possibile fare riferimento a determinati assembly del framework a cui non è possibile fare riferimento in altro modo. |
| TargetFrameworkVersion | .NET | Versione di .NET Framework richiesta per eseguire l'applicazione in corso di compilazione. Se si imposta questa proprietà, è possibile fare riferimento a determinati assembly del framework a cui non è possibile fare riferimento in altro modo. |
| TreatWarningsAsErrors | .NET | Parametro booleano che, se impostato su `true`, fa sì che tutti gli avvisi vengano considerati errori. Questo parametro è equivalente all'opzione del compilatore `/nowarn`. |
| UseHostCompilerIfAvailable | .NET | Parametro booleano che, se impostato su `true`, fa sì che l'attività di compilazione utilizzi l'oggetto del compilatore in-process, se disponibile. Questo parametro viene usato solo da Visual Studio. |
| Utf8Output | .NET | Parametro booleano che, se impostato su `true`, registra l'output del compilatore usando la codifica UTF-8. Questo parametro è equivalente all'opzione del compilatore `/utf8Output`. |
| VbcToolPath | Visual Basic | Percorso facoltativo che indica un altro percorso di *vbc.exe* quando viene eseguito l'override della versione corrente di *vbc.exe*. |
| VbcVerbosity | Visual Basic | Specifica il livello di dettaglio dell'Visual Basic output del compilatore. I valori validi sono "Non interattivo", "Normale" (valore predefinito) o "Dettagliato". |
| VisualStudioVersion | Tutti | Specifica in quale versione di Visual Studio deve essere considerato in esecuzione questo progetto. Se non si specifica questa proprietà, MSBuild la imposta su un valore predefinito appropriato.<br /><br /> Questa proprietà viene usata in diversi tipi di progetto per specificare il set di destinazioni usate per la compilazione. Se `ToolsVersion` è impostato su 4.0 o un valore superiore per un progetto, la proprietà `VisualStudioVersion` viene usata per specificare quale set di strumenti secondario usare. Per altre informazioni, vedere [Set di strumenti MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Specifica un elenco di avvisi da considerare come errori. Questo parametro è equivalente all'opzione del compilatore `/warnaserror`. |
| WarningsNotAsErrors | .NET | Specifica un elenco di avvisi che non vengono considerati errori. Questo parametro è equivalente all'opzione del compilatore `/warnaserror`. |
| Win32Manifest | .NET | Nome del file manifesto che deve essere incorporato nell'assembly finale. Questo parametro è equivalente all'opzione del compilatore `/win32Manifest`. |
| Win32Resource | .NET | Nome file della risorsa Win32 da incorporare nell'assembly finale. Questo parametro è equivalente all'opzione del compilatore `/win32resource`. |

## <a name="see-also"></a>Vedi anche

- [Elementi di progetto MSBuild comuni](../msbuild/common-msbuild-project-items.md)
- [Metadati dell'elemento MSBuild comuni](common-msbuild-item-metadata.md)
- [MSBuild Proprietà riservate e note](msbuild-reserved-and-well-known-properties.md)
- [MSBuild informazioni di riferimento per i progetti .NET SDK](/dotnet/core/project-sdk/msbuild-props)
