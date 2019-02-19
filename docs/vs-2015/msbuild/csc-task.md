---
title: Attività Csc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3cab96aece51252c5a847e07fc3863e6b6f0bf5
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54766189"
---
# <a name="csc-task"></a>Attività Csc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Esegue il wrap di CSC.exe e produce file eseguibili (con estensione EXE), librerie a collegamento dinamico (con estensione DLL) o moduli di codice (con estensione NETMODULE). Per altre informazioni su CSC.exe, vedere [Opzioni del compilatore C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Csc` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica directory aggiuntive in cui cercare i riferimenti. Per altre informazioni, vedere [/lib (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Parametro `String` facoltativo.<br /><br /> Specifica uno o più moduli che devono fare parte dell'assembly. Per altre informazioni, vedere [/addmodule (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, compila codice che usa la parola chiave [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Per altre informazioni, vedere [/unsafe (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Parametro `String` facoltativo.<br /><br /> Specifica il file di configurazione dell'applicazione contenente le impostazioni di associazione dell'assembly.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se il calcolo di interi che supera i limiti del tipo di dati genera un'eccezione in fase di esecuzione. Per altre informazioni, vedere [/checked (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Per altre informazioni, vedere [/codepage (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di debug. `DebugType` può essere `full` o `pdbonly`. Il valore predefinito è `full`, che consente di associare un debugger a un programma in esecuzione. La specifica di `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma assembler viene visualizzato solo quando il programma in esecuzione è collegato al debugger.<br /><br /> Questo parametro esegue l'override del parametro `EmitDebugInformation`.<br /><br /> Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Parametro `String` facoltativo.<br /><br /> Definisce i simboli del preprocessore. Per altre informazioni, vedere [/define (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che si vuole un'assembly completamente firmata. Se `false`, specifica che si vuole solo posizionare la chiave pubblica nell'assembly.<br /><br /> Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`.<br /><br /> Per altre informazioni, vedere [/delaysign (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Specifica l'elenco di avvisi da disabilitare. Per altre informazioni, vedere [/nowarn (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora commenti sulla documentazione in un file XML. Per altre informazioni, vedere [/doc (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> If `true`, l'attività genera informazioni di debug e le inserisce in un file di database di programma (con estensione PDB). Se `false`, l'attività non genera alcuna informazione di debug. Il valore predefinito è `false`. Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Offre un modo pratico per segnalare a Microsoft un errore interno di C#. Il valore di questo parametro può essere `prompt`, `send` o `none`. Se il parametro è impostato su `prompt`, si riceve un avviso quando si verifica un errore interno del compilatore. L'avviso consente di inviare elettronicamente una segnalazione a Microsoft. Se il parametro è impostato su `send`, viene inviato automaticamente un report sui bug. Se il parametro è impostato su `none`, l'errore viene segnalato solo nell'output di testo del compilatore. Il valore predefinito è `none`. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica le dimensioni delle sezioni nel file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica il percorso assoluto al file nell'output del compilatore. Se `false`, specifica il nome del file. Il valore predefinito è `false`. Per altre informazioni, vedere [/fullpaths (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Per altre informazioni, vedere [/keycontainer (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per altre informazioni, vedere [/keyfile (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione del linguaggio da usare. Per altre informazioni, vedere [/langversion (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Crea un collegamento a una risorsa [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nel file di output. Il file di risorse non viene inserito nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/linkresource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [/linkresource (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso del metodo `Main`. Per altre informazioni, vedere [/main (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly di cui fa parte il modulo.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, indica al compilatore di non eseguire la compilazione con il file csc.rsp. Per altre informazioni, vedere [/noconfig (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, elimina la visualizzazione dei messaggi informativi del compilatore. Per altre informazioni, vedere [/nologo (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce l'importazione di mscorlib.dll, che definisce l'intero spazio dei nomi di sistema. Usare questo parametro se si vuole definire o creare uno spazio dei nomi e oggetti di sistema personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, non includere il manifesto Win32 predefinito.|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, abilita le ottimizzazioni. Se `false`, disabilita le ottimizzazioni. Per altre informazioni, vedere [/optimize (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome del file di output. Per altre informazioni, vedere [/out (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome file delle informazioni di debug. Il nome predefinito è il nome file di output con estensione PDB.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Il valore di questo parametro può essere `x86`, `x64` o `anycpu`. Il valore predefinito è `anycpu`. Per altre informazioni, vedere [/platform (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'attività per importare informazioni di tipi pubblico dagli elementi specificati nel progetto corrente. Per altre informazioni, vedere [/reference (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> È possibile specificare un alias di riferimento [!INCLUDE[csprcs](../includes/csprcs-md.md)] in un file [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aggiungendo i metadati `Aliases` all'elemento originale di "riferimento". Ad esempio, per impostare l'alias "LS1" nella riga di comando CSC seguente:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> è necessario usare:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Inserisce una risorsa [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nel file di output.<br /><br /> Gli elementi passati a questo parametro possono avere voci di metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al parametro `identifier` dell'opzione `/resource` e `Access` corrisponde al parametro `accessibility-modifier`. Per altre informazioni, vedere [/resource (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Parametro `String` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Per altre informazioni, vedere [@ (specifica di un file di risposta)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica uno o più file di origine [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che crea una libreria di codice, `exe`, che crea un'applicazione console, `module`, che crea un modulo o `winexe`, che crea un programma Windows. Il valore predefinito è `library`. Per altre informazioni, vedere [/target (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tutti gli avvisi vengono considerati come errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di usare l'oggetto del compilatore in corso, se disponibile. Usato solo da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore tramite la codifica UTF-8. Per altre informazioni, vedere [/utf8output (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Parametro `Int32` facoltativo.<br /><br /> Specifica il livello di avviso da visualizzare nel compilatore. Per altre informazioni, vedere [/warn (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Questo parametro è utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file con estensione ICO nell'assembly, che dà al file di output l'aspetto voluto in Esplora file. Per altre informazioni, vedere [/win32icon (C# Compiler Options)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Parametro `String` facoltativo.<br /><br /> Specifica il manifesto Win32 da includere.|  
|`Win32Resource`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorsa Win32 (estensione RES) nel file di output . Per altre informazioni, vedere [/win32res (C# Compiler Options)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe `Microsoft.Build.Tasks.ManagedCompiler`, che eredita dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/tooltaskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `Csc` per compilare un eseguibile dai file di origine nella raccolta di elementi `Compile`.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)
