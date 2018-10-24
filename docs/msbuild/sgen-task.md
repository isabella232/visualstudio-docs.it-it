---
title: Attività SGen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89a5285e304e74aba01f81d8ec9bfc5017677a7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919182"
---
# <a name="sgen-task"></a>SGen (attività)
Crea un assembly di serializzazione XML per i tipi presenti nell'assembly specificato. Questa attività esegue il wrapping dello strumento per la generazione di serializzatori XML *Sgen.exe*. Per altre informazioni, vedere [Strumento per la generazione di serializzatori XML (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).  

## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `SGen` .  


| Parametro | Descrizione |
|-----------------------------| - |
| `BuildAssemblyName` | Parametro `String` obbligatorio.<br /><br /> Assembly per cui generare il codice di serializzazione. |
| `BuildAssemblyPath` | Parametro `String` obbligatorio.<br /><br /> Percorso dell'assembly per cui generare il codice di serializzazione. |
| `DelaySign` | Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che si vuole un'assembly completamente firmata. Se `false`, specifica che si vuole solo posizionare la chiave pubblica nell'assembly.<br /><br /> Questo parametro ha effetto solo se usato con il parametro `KeyFile` o `KeyContainer`. |
| `KeyContainer` | Parametro `String` facoltativo.<br /><br /> Specifica un contenitore che include una coppia di chiavi. Tale parametro firmerà l'assembly mediante l'inserimento di una chiave pubblica nel relativo manifesto. L'attività firmerà quindi l'assembly finale con la chiave privata. |
| `KeyFile` | Parametro `String` facoltativo.<br /><br /> Specifica una coppia di chiavi o una chiave pubblica da usare per firmare un assembly. Durante la compilazione la chiave pubblica verrà inserita nel manifesto dell'assembly, mentre l'assembly finale verrà firmato con la chiave privata. |
| `Platform` | Parametro `String` facoltativo.<br /><br /> Ottiene o imposta la piattaforma del compilatore usata per generare l'assembly di output. Il valore di questo parametro può essere `x86`, `x64` o `anycpu`. Il valore predefinito è `anycpu`. |
| `References` | Parametro `String[]` facoltativo.<br /><br /> Specifica gli assembly a cui fanno riferimento i tipi che richiedono la serializzazione XML. |
| `SdkToolsPath` | Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio *resgen.exe*. |
| `SerializationAssembly` | Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'assembly di serializzazione generato. |
| `SerializationAssemblyName` | Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly di serializzazione generato. |
| `ShouldGenerateSerializer` | Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, l'attività SGen deve generare un assembly di serializzazione. |
| `Timeout` | Parametro `Int32` facoltativo.<br /><br /> Specifica la quantità di tempo, in millisecondi, dopo i quali l'eseguibile dell'attività viene terminato. Il valore predefinito è `Int.MaxValue`, con cui si indica che non esiste alcun periodo di timeout. |
| `ToolPath` | Parametro `String` facoltativo.<br /><br /> Specifica la posizione da cui l'attività caricherà il file eseguibile sottostante (*sgen.exe*). Se questo parametro non è specificato, viene usato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Types` | Parametro `String[]` facoltativo.<br /><br /> Ottiene o imposta un elenco di tipi specifici per cui generare il codice di serializzazione. L'attività SGen genererà il codice di serializzazione solo per questi tipi. |
| `UseProxyTypes` | Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, l'attività SGen genera il codice di serializzazione solo per i tipi proxy del servizio Web XML. |

## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  

## <a name="see-also"></a>Vedere anche  
 [Attività MSBuild](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)