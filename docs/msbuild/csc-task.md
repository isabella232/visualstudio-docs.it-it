---
title: Attività Csc | Microsoft Docs
description: Questo articolo descrive l'attività Csc di MSBuild, che esegue il wrapping del compilatore C#, csc.exe e produce file .exe, .dll o netmodule.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10a63b114379f56ca5f253f853a1ff6bdd6c60dc
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588475"
---
# <a name="csc-task"></a>Csc (attività)

Esegue il wrapping di *csc.exe* e produce file eseguibili (*EXE*), librerie a collegamento dinamico (file *DLL*) o moduli di codice (file *NETMODULE*). Per altre informazioni su *csc.exe*, vedere [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Csc` .

| Parametro | Descrizione |
|------------------------------| - |
| `AdditionalLibPaths` | Parametro `String[]` facoltativo.<br /><br /> Specifica directory aggiuntive in cui cercare i riferimenti. Per altre informazioni, vedere [-lib (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Parametro `String` facoltativo.<br /><br /> Specifica uno o più moduli che devono fare parte dell'assembly. Per altre informazioni, vedere [-addmodule (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, compila codice che usa la parola chiave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Per altre informazioni, vedere [-unsafe (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option) |
| `ApplicationConfiguration` | Parametro `String` facoltativo.<br /><br /> Specifica il file di configurazione dell'applicazione contenente le impostazioni di associazione dell'assembly. |
| `BaseAddress` | Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime di .NET Framework. Per altre informazioni, vedere [-baseaddress (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Parametro `Boolean` facoltativo.<br /><br /> Specifica se il calcolo di interi che supera i limiti del tipo di dati genera un'eccezione in fase di esecuzione. Per altre informazioni, vedere [-checked (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Per altre informazioni, vedere [-codepage (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Parametro `String` facoltativo.<br /><br /> Specifica il tipo di debug. `DebugType` può essere `full` o `pdbonly`. Il valore predefinito è `full`, che consente di associare un debugger a un programma in esecuzione. La specifica di `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma assembler viene visualizzato solo quando il programma in esecuzione è collegato al debugger.<br /><br /> Questo parametro esegue l'override del parametro `EmitDebugInformation`.<br /><br /> Per altre informazioni, vedere [-debug (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Parametro `String` facoltativo.<br /><br /> Definisce i simboli del preprocessore. Per altre informazioni, vedere [-define (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che si vuole solo posizionare la chiave pubblica nell'assembly. Se `false` , specifica che si vuole un assembly con firma completa<br /><br /> Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`.<br /><br /> Per altre informazioni, vedere [-delaysign (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Parametro `Boolean` facoltativo.<br/><br/> Se `true`, l'output del compilatore è un assembly il cui contenuto binario è identico in tutte le compilazioni se gli input sono identici.<br/><br/>Per altre informazioni, vedere [-deterministic (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Parametro `String` facoltativo.<br /><br /> Specifica l'elenco di avvisi da disabilitare. Per altre informazioni, vedere [-nowarn (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) |
| `DocumentationFile` | Parametro `String` facoltativo.<br /><br /> Elabora commenti sulla documentazione in un file XML. Per altre informazioni, vedere [-doc (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) |
| `EmbedAllSources` | Parametro `Boolean` facoltativo.<br /><br /> Incorporare tutti i file di origine nel file PDB. Per altre informazioni, vedere [-embed (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically) |
| `EmitDebugInformation` | Parametro `Boolean` facoltativo.<br /><br /> If `true`, l'attività genera informazioni di debug e le inserisce in un file di database di programma (con estensione PDB). Se `false`, l'attività non genera alcuna informazione di debug. Il valore predefinito è `false`. Per altre informazioni, vedere [-debug (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Parametro `String` facoltativo.<br /><br /> Offre un modo pratico per segnalare a Microsoft un errore interno di C#. Il valore di questo parametro può essere `prompt`, `send` o `none`. Se il parametro è impostato su `prompt`, si riceve un avviso quando si verifica un errore interno del compilatore. L'avviso consente di inviare elettronicamente una segnalazione a Microsoft. Se il parametro è impostato su `send`, viene inviato automaticamente un report sui bug. Se il parametro è impostato su `none`, l'errore viene segnalato solo nell'output di testo del compilatore. Il valore predefinito è `none`. Per altre informazioni, vedere [-errorreport (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Parametro `Int32` facoltativo.<br /><br /> Specifica le dimensioni delle sezioni nel file di output. Per altre informazioni, vedere [-filealign (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica il percorso assoluto al file nell'output del compilatore. Se `false`, specifica il nome del file. Il valore predefinito è `false`. Per altre informazioni, vedere [-fullpaths (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Per altre informazioni, vedere [-keycontainer (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per altre informazioni, vedere [-keyfile (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Parametro `String` facoltativo.<br /><br /> Specifica la versione del linguaggio da usare. Per altre informazioni, vedere [-langversion (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Crea un collegamento a una risorsa .NET Framework nel file di output. Il file di risorse non viene inserito nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/linkresource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [-linkresource (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Parametro `String` facoltativo.<br /><br /> Specifica il percorso del metodo `Main`. Per altre informazioni, vedere [-main (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly di cui fa parte il modulo. |
| `NoConfig` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, indica al compilatore di non eseguire la compilazione con il file *csc.rsp*. Per altre informazioni, vedere [-noconfig (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, elimina la visualizzazione dei messaggi informativi del compilatore. Per altre informazioni, vedere [-nologo (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Parametro `Boolean` facoltativo.<br /><br /> Se `true` , impedisce l'importazione di *mscorlib.dll*, che definisce l'intero spazio dei nomi System. Usare questo parametro se si vuole definire o creare uno spazio dei nomi e oggetti di sistema personalizzati. Per altre informazioni, vedere [-nostdlib (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, non includere il manifesto Win32 predefinito. |
| `Optimize` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, abilita le ottimizzazioni. Se `false`, disabilita le ottimizzazioni. Per altre informazioni, vedere [-optimize (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome del file di output. Per altre informazioni, vedere [-out (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Parametro `String` facoltativo.<br /><br /> Specifica il nome del file di assembly di riferimento di output. Per altre informazioni, vedere [-refout (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option) |
| `PdbFile` | Parametro `String` facoltativo.<br /><br /> Specifica il nome file delle informazioni di debug. Il nome predefinito è il nome del file di output con estensione *pdb.* |
| `Platform` | Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Il valore di questo parametro può essere `x86`, `x64` o `anycpu`. Il valore predefinito è `anycpu`. Per altre informazioni, vedere [-platform (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option) |
| `References` | Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica l'attività per importare informazioni di tipi pubblico dagli elementi specificati nel progetto corrente. Per altre informazioni, vedere [-reference (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> È possibile specificare un alias di riferimento C# in un file MSBuild aggiungendo i metadati `Aliases` all'elemento "Reference" originale. Ad esempio, per impostare l'alias "LS1" nella riga di comando Csc seguente:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> è necessario usare:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Incorpora una risorsa di .NET Framework nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/resource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [-resource (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Parametro `String` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Per altre informazioni, vedere [@ (specificare il file di risposta)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica uno o più file di origine C#. |
| `TargetType` | Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che crea una libreria di codice, `exe`, che crea un'applicazione console, `module`, che crea un modulo o `winexe`, che crea un programma Windows. Il valore predefinito è `library`. Per altre informazioni, vedere [-target (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tutti gli avvisi vengono considerati come errori. Per altre informazioni, vedere [-warnaserror (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di usare l'oggetto del compilatore in corso, se disponibile. Usata solo da Visual Studio. |
| `Utf8Output` | Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore tramite la codifica UTF-8. Per altre informazioni, vedere [-utf8output (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Parametro `Int32` facoltativo.<br /><br /> Specifica il livello di avviso da visualizzare nel compilatore. Per altre informazioni, vedere [-warn (opzioni del compilatore C#).](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) |
| `WarningsAsErrors` | Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per altre informazioni, vedere [-warnaserror (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per altre informazioni, vedere [-warnaserror (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro è utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`. |
| `Win32Icon` | Parametro `String` facoltativo.<br /><br /> Inserisce un file *con estensione ico* nell'assembly, che fornisce al file di output l'aspetto **desiderato** Esplora file . Per altre informazioni, vedere [-win32icon (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Parametro `String` facoltativo.<br /><br /> Specifica il manifesto Win32 da includere. |
| `Win32Resource` | Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorsa Win32 ( con estensione *res*) nel file di output. Per altre informazioni, vedere [-win32res (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Esempio

Nell'esempio seguente viene usata l'attività `Csc` per compilare un eseguibile dai file di origine nella raccolta di elementi `Compile`.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
