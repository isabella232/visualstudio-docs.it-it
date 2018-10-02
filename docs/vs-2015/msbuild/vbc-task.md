---
title: Attività Vbc | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0457456651e233c44e5e8e5ae44e30013e0de0c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540763"
---
# <a name="vbc-task"></a>Attività Vbc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività Vbc](https://docs.microsoft.com/visualstudio/msbuild/vbc-task).  
  
  
Esegue il wrapping di vbc.exe, un compilatore che genera file eseguibili con estensione exe, librerie a collegamento dinamico con estensione dll o moduli di codice con estensione netmodule. Per altre informazioni su vbc.exe, vedere [Visual Basic Command-Line Compiler](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c) (Compilatore della riga di comando di Visual Basic).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Vbc` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica cartelle aggiuntive in cui eseguire la ricerca degli assembly specificati nell'attributo References.|  
|`AddModules`|Parametro `String[]` facoltativo.<br /><br /> Fa sì che il compilatore renda disponibili per il progetto in compilazione tutte le informazioni sui tipi presenti nei file specificati. Questo parametro corrisponde all'opzione [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) del compilatore vbc.exe.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base della DLL. Questo parametro corrisponde all'opzione [/baseaddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) del compilatore vbc.exe.|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Questo parametro corrisponde all'opzione [/codepage](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) del compilatore vbc.exe.|  
|`DebugType`|Parametro `String[]` facoltativo.<br /><br /> Causa la generazione di informazioni di debug da parte del compilatore. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Il valore predefinito è `full`, che consente di collegare un debugger al programma in esecuzione. Il valore `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma consente la visualizzazione di codice in linguaggio assembly solo se il programma in esecuzione è collegato al debugger. Per altre informazioni, vedere [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Parametro `String[]` facoltativo.<br /><br /> Definisce le costanti del compilatore condizionali. Le coppie simbolo/valore sono separate da punti e virgola e vengono specificate tramite la sintassi seguente:<br /><br /> *simbolo1* `=` *valore1* `;` *simbolo2* `=` *valore2*<br /><br /> Questo parametro corrisponde all'opzione [/define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) del compilatore vbc.exe.|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività inserisce la chiave pubblica nell'assembly. Se `false`, l'attività firma l'assembly completamente. Il valore predefinito è `false`. Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`. Questo parametro corrisponde all'opzione [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) del compilatore vbc.exe.|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Non visualizza gli avvisi specificati. È sufficiente specificare la parte numerica dell'identificatore dell'avviso. Se si specificano più avvisi, usare il punto e virgola per separarli. Questo parametro corrisponde all'opzione [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) del compilatore vbc.exe.|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora i commenti relativi alla documentazione nel file XML specificato. Questo parametro esegue l'override dell'attributo `GenerateDocumentation`. Per altre informazioni, vedere [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività genera informazioni di debug e le inserisce in un file con estensione pdb. Per altre informazioni, vedere [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità di segnalazione degli errori interni da parte dell'attività. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Se è specificato il valore `prompt` e si verifica un errore interno del compilatore, viene chiesto se si vogliono inviare i dati dell'errore a Microsoft.<br /><br /> Se è specificato il valore `send` e si verifica un errore interno del compilatore, i dati dell'errore vengono inviati a Microsoft.<br /><br /> Il valore predefinito è `none`, in base al quale gli errori vengono segnalati solo sotto forma di output di testo.<br /><br /> Questo parametro corrisponde all'opzione [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) del compilatore vbc.exe.|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica, in byte, il punto in cui allineare le sezioni del file di output. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Questo parametro corrisponde all'opzione [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) del compilatore vbc.exe.|  
|`GenerateDocumentation`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, vengono generate informazioni di documentazione, che vengono inserite in un file XML con il nome del file eseguibile o della libreria che l'attività sta creando. Per altre informazioni, vedere [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Importa gli spazi dei nomi dalle raccolte di elementi specificati. Questo parametro corrisponde all'opzione [/imports](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) del compilatore vbc.exe.|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Questo parametro corrisponde all'opzione [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) del compilatore vbc.exe.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per altre informazioni, vedere [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|[String] facoltativo (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametro.<br /><br /> Specifica la versione del linguaggio: "9" o "10".|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Crea un collegamento a una risorsa .NET Framework nel file di output. Il file di risorse non viene inserito nel file di output. Questo parametro corrisponde all'opzione [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) del compilatore vbc.exe.|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica la classe o il modulo che contiene la procedura `Sub Main`. Questo parametro corrisponde all'opzione [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) del compilatore vbc.exe.|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica l'assembly di cui il modulo fa parte.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Specifica che il compilatore non deve usare il file vbc.rsp. Questo parametro corrisponde al parametro [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) del compilatore vbc.exe.|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, elimina la visualizzazione dei messaggi informativi del compilatore. Questo parametro corrisponde all'opzione [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) del compilatore vbc.exe.|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Indica al compilatore di non fare riferimento alle librerie standard. Questo parametro corrisponde all'opzione [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) del compilatore vbc.exe.|  
|`NoVBRuntimeReference`|Parametro `Boolean` facoltativo.<br /><br /> Solo per uso interno. Se true, viene impedito il riferimento automatico a Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività disabilita la visualizzazione di tutti gli avvisi. Per altre informazioni, vedere [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, le ottimizzazioni del compilatore vengono abilitate. Questo parametro corrisponde all'opzione [/optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) del compilatore vbc.exe.|  
|`OptionCompare`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità con cui vengono confrontate le stringhe. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Il valore `binary` specifica l'uso di confronti tra stringhe binarie da parte dell'attività. Il valore `text` specifica l'uso di confronti tra stringhe di testo da parte dell'attività. Il valore predefinito di questo parametro è `binary`. Questo parametro corrisponde all'opzione [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) del compilatore vbc.exe.|  
|`OptionExplicit`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la dichiarazione esplicita delle variabili è obbligatoria. Questo parametro corrisponde all'opzione [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) del compilatore vbc.exe.|  
|`OptionInfer`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, è consentita l'inferenza del tipo delle variabili.|  
|`OptionStrict`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività applica la semantica dei tipi strict per limitare le conversioni implicite di tipi. Questo parametro corrisponde all'opzione [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) del compilatore vbc.exe.|  
|`OptionStrictType`|Parametro `String` facoltativo.<br /><br /> Specifica quale semantica dei tipi strict genera un avviso. Al momento è supportato solo "custom". Questo parametro corrisponde all'opzione [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) del compilatore vbc.exe.|  
|`OutputAssembly`|Parametro di ouput facoltativo `String`.<br /><br /> Specifica il nome del file di output. Questo parametro corrisponde all'opzione [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) del compilatore vbc.exe.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Il valore di questo parametro può essere `x86`, `x64`, `Itanium` o `anycpu`. Il valore predefinito è `anycpu`. Questo parametro corrisponde all'opzione [/platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) del compilatore vbc.exe.|  
|`References`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'attività per importare informazioni di tipi pubblico dagli elementi specificati nel progetto corrente. Questo parametro corrisponde all'opzione [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) del compilatore vbc.exe.|  
|`RemoveIntegerChecks`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, disabilita i controlli degli errori di overflow degli integer. Il valore predefinito è `false`. Questo parametro corrisponde all'opzione [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) del compilatore vbc.exe.|  
|`Resources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Incorpora una risorsa di .NET Framework nel file di output. Questo parametro corrisponde all'opzione [/resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) del compilatore vbc.exe.|  
|`ResponseFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Questo parametro corrisponde all'opzione [@ (specificare il file di risposta)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) del compilatore vbc.exe.|  
|`RootNamespace`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per tutte le dichiarazioni di tipo. Questo parametro corrisponde all'opzione [/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) del compilatore vbc.exe.|  
|`SdkPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso dei file mscorlib.dll e microsoft.visualbasic.dll. Questo parametro corrisponde all'opzione [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) del compilatore vbc.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica uno o più file di origine [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`TargetCompactFramework`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene usato [!INCLUDE[Compact](../includes/compact-md.md)]. Questa opzione corrisponde all'opzione [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) del compilatore vbc.exe.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che crea una libreria di codice, `exe`, che crea un'applicazione console, `module`, che crea un modulo o `winexe`, che crea un programma Windows. Il valore predefinito è `library`. Questo parametro corrisponde all'opzione [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) del compilatore vbc.exe.|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, con cui si indica che non esiste alcun periodo di timeout.|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica la posizione da cui l'attività caricherà il file eseguibile sottostante (vbc.exe). Se questo parametro non è specificato, viene usato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tutti gli avvisi vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di usare l'oggetto del compilatore in corso, se disponibile. Usato solo da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore tramite la codifica UTF-8. Questo parametro corrisponde all'opzione [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) del compilatore vbc.exe.|  
|`Verbosity`|Parametro `String` facoltativo.<br /><br /> Specifica il livello di dettaglio dell'output del compilatore. Il livello di dettaglio può essere `Quiet`, `Normal` (impostazione predefinita) o `Verbose`.|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per altre informazioni, vedere [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Questo parametro è utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file con estensione ICO nell'assembly, che dà al file di output l'aspetto voluto in Esplora file. Questo parametro corrisponde all'opzione [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) del compilatore vbc.exe.|  
|`Win32Resources`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorsa Win32 (estensione RES) nel file di output . Questo parametro corrisponde all'opzione [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) del compilatore vbc.exe.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/tooltaskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguita la compilazione di un progetto [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Basic Command-Line Compiler](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)  (Compilatore da riga di comando di Visual Basic)  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



