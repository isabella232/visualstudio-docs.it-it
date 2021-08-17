---
title: Attività GenerateDeploymentManifest | Microsoft Docs
description: Informazioni su come usare l MSBuild'attività GenerateDeploymentManifest per generare un manifesto ClickOnce distribuzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 06b40841507812d7d2892a57f24995f580c8be9a3e79c52286835336f462390f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427834"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest (attività)

Genera un manifesto ClickOnce distribuzione. Un manifesto della distribuzione ClickOnce descrive la distribuzione di un'applicazione definendo un'identità univoca per la distribuzione, identificando i tratti di distribuzione, ad esempio l'installazione o la modalità online, specificando le impostazioni di aggiornamento dell'applicazione e i percorsi di aggiornamento e indicando il manifesto dell'applicazione ClickOnce corrispondente.

## <a name="parameters"></a>Parametri

La tabella seguente descrive i parametri dell'attività `GenerateDeploymentManifest`.

| Parametro | Descrizione |
|--------------------------| - |
| `AssemblyName` | Parametro `String` facoltativo.<br /><br /> Specifica il campo `Name` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, il nome viene dedotto dal parametro `EntryPoint` o `InputManifest`. Se non è possibile dedurre il nome, viene generato un errore. |
| `AssemblyVersion` | Parametro `String` facoltativo.<br /><br /> Specifica il campo `Version` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non è specificato, l'attività usa il valore "1.0.0.0". |
| `CreateDesktopShortcut` | Parametro `Boolean` facoltativo.<br /><br /> Se true, durante l'installazione dell'applicazione ClickOnce viene creata un'icona sul desktop. |
| `DeploymentUrl` | Parametro `String` facoltativo.<br /><br /> Specifica il percorso di aggiornamento per l'applicazione. Se questo parametro non è specificato, non viene definito alcun percorso di aggiornamento per l'applicazione. Se tuttavia il parametro `UpdateEnabled` è impostato su `true`, è necessario specificare il percorso di aggiornamento. Il valore specificato deve essere un percorso URL o UNC completo. |
| `Description` | Parametro `String` facoltativo.<br /><br /> Specifica una descrizione facoltativa per l'applicazione. |
| `DisallowUrlActivation` | Parametro `Boolean` facoltativo.<br /><br /> Specifica se l'applicazione deve essere eseguita automaticamente quando viene aperta tramite un URL. Se questo parametro è `true` , l'applicazione può essere avviata solo dal menu **Start.** Il valore predefinito di questo parametro è `false`. Questo input è applicabile solo quando il valore del parametro `Install` è impostato su `true`. |
| `EntryPoint` | Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Indica il punto di ingresso per l'assembly del manifesto generato. Per un ClickOnce di distribuzione, questo input specifica il ClickOnce dell'applicazione.<br /><br />Se non viene specificato il parametro attività `EntryPoint`, il tag `<customHostSpecified>` viene inserito come figlio del tag `<entryPoint>`, ad esempio:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> È possibile aggiungere dipendenze DLL al manifesto dell'applicazione seguendo questa procedura:<br /><br /> 1. Risolvere i riferimenti all'assembly con una chiamata a <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. Passare l'output dell'attività precedente e l'assembly stesso a <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. Passare le dipendenze usando il `Dependencies` parametro a <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> . |
| `ErrorReportUrl` | Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Specifica l'URL della pagina Web visualizzata nelle finestre di dialogo durante le installazioni ClickOnce. |
| `InputManifest` | Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML di input da usare come base per il generatore del manifesto. In questo modo è possibile applicare nel manifesto di output dati strutturati, ad esempio definizioni del manifesto personalizzate. L'elemento radice del documento XML deve essere un nodo assembly nello spazio dei nomi asmv1. |
| `Install` | Parametro `Boolean` facoltativo.<br /><br /> Specifica se si tratta di un'applicazione installata o di un'applicazione disponibile solo online. Se questo parametro è , l'applicazione verrà installata nel `true` menu **Start** dell'utente e potrà essere rimossa tramite la finestra di dialogo Installazione applicazioni .  Se questo parametro è `false`, l'applicazione è destinata all'uso online da una pagina Web. Il valore predefinito di questo parametro è `true`. |
| `MapFileExtensions` | Parametro `Boolean` facoltativo.<br /><br /> Specifica se viene utilizzato il mapping *dell'estensione* di file deploy. Se questo parametro è `true` , ogni file di programma viene pubblicato con estensione *deploy.* Questa opzione è utile per la sicurezza del server Web per limitare il numero di estensioni di file che devono essere sbloccate per abilitare la ClickOnce dell'applicazione. Il valore predefinito di questo parametro è `false`. |
| `MaxTargetPath` | Parametro `String` facoltativo.<br /><br /> Specifica la lunghezza massima consentita di un percorso di file in una distribuzione ClickOnce'applicazione. Se questo parametro è specificato, la lunghezza di ogni percorso di file dell'applicazione viene verificata a fronte di tale limite. Per tutti gli elementi che superano il limite verrà visualizzato un avviso di compilazione. Se questo input non è specificato o è uguale a zero, non viene eseguita alcuna verifica. |
| `MinimumRequiredVersion` | Parametro `String` facoltativo.<br /><br /> Specifica se è possibile ignorare l'aggiornamento. Se viene usata una versione precedente rispetto a quella minima richiesta, non sarà possibile ignorare l'aggiornamento. Questo parametro è applicabile solo quando il parametro `Install` è impostato su `true`. |
| `OutputManifest` | Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file del manifesto di output generato. Se questo parametro non è specificato, il nome del file di output viene dedotto dall'identità del manifesto generato. |
| `Platform` | Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma di destinazione dell'applicazione. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Il valore predefinito è `AnyCPU`. |
| `Product` | Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'identità del manifesto generato. Questo nome viene usato per il collegamento nel menu **Start** e fa parte del nome visualizzato nella finestra di dialogo **Installazione applicazioni**. |
| `Publisher` | Parametro `String` facoltativo.<br /><br /> Specifica l'editore dell'applicazione. Se questo parametro non è specificato, il nome viene dedotto dall'utente registrato o dall'identità del manifesto generato. Questo nome viene usato per la cartella nel menu **Start** e fa parte del nome visualizzato nella finestra di dialogo **Installazione applicazioni**. |
| `SuiteNamel` | Parametro `String` facoltativo.<br /><br /> Specifica il nome della cartella nel menu **Start** in cui si trova l'applicazione dopo ClickOnce distribuzione. |
| `SupportUrl` | Parametro `String` facoltativo.<br /><br /> Specifica il collegamento visualizzato nella finestra di dialogo **Installazione** applicazioni per l'applicazione. Il valore specificato deve essere un percorso URL o UNC completo. |
| `TargetCulture` | Parametro `String` facoltativo.<br /><br /> Identifica le impostazioni cultura dell'applicazione e specifica il campo `Language` relativo all'identità dell'assembly per il manifesto generato. Se questo parametro non viene specificato, si presuppone che l'applicazione sia indipendente dalle impostazioni cultura. |
| `TrustUrlParameters` | Parametro `Boolean` facoltativo.<br /><br /> Specifica se i parametri della stringa di query dell'URL devono essere disponibili per l'applicazione. Il valore predefinito del parametro è `false` e indica che i parametri non saranno disponibili per l'applicazione. |
| `UpdateEnabled` | Parametro `Boolean` facoltativo.<br /><br /> Indica se l'applicazione è abilitata per gli aggiornamenti. Il valore predefinito di questo parametro è `false`. Questo parametro è applicabile solo quando il parametro `Install` è impostato su `true`. |
| `UpdateInterval` | Parametro `Int32` facoltativo.<br /><br /> Specifica l'intervallo di aggiornamento per l'applicazione. Il valore predefinito di questo parametro è zero. Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`. |
| `UpdateMode` | Parametro `String` facoltativo.<br /><br /> Specifica se è necessario verificare gli aggiornamenti in primo piano prima dell'avvio dell'applicazione o in background durante l'esecuzione dell'applicazione. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Il valore predefinito di questo parametro è `Background`. Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`. |
| `UpdateUnit` | Parametro `String` facoltativo.<br /><br /> Specifica le unità per il parametro `UpdateInterval`. Per il parametro è possibile specificare i valori seguenti:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Questo parametro è applicabile solo quando i parametri `Install` e `UpdateEnabled` sono entrambi impostati su `true`. |

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.GenerateManifestBase> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco dei parametri della classe Task, vedere [Classe di base Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest (attività)](../msbuild/generateapplicationmanifest-task.md)
- [SignFile (attività)](../msbuild/signfile-task.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
