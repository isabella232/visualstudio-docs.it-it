---
title: Attività FXC | Microsoft Docs
description: Informazioni sui parametri che l'MSBuild FXC usa per i compilatori di shader HLSL nel processo di compilazione.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 7f98bc7790f3d5e8ae4e28e83428ce350e2e7430a2e6327f3a2a559e86e37370
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427847"
---
# <a name="fxc-task"></a>Attività FXC

Usare i compilatori di shader HLSL nel processo di compilazione.

## <a name="parameters"></a>Parametri

Nella tabella seguente vengono descritti i parametri dell'attività **FXC**.

|Parametro|Descrizione|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parametro **string[]** facoltativo.<br/><br/>Specifica una o più directory da aggiungere al percorso di inclusione. Usare il punto e virgola (;) come delimitatore per più percorsi.<br/><br/>Usare `/I[path]`.|
|**Opzioni aggiuntive**|Parametro **stringa facoltativo.**|
|**AllResourcesBound**|Parametro **bool** facoltativo.<br/><br/>Il compilatore presupporrà che tutte le risorse a cui uno shader può fare riferimento siano associate e in uno stato corretto per la durata dell'esecuzione dello shader. Disponibile per Modello shader 5.1 e versioni successive.<br/><br/>Usare `/all_resources_bound`.|
|**AssemblerOutput**|Parametro **stringa facoltativo.**<br/><br/>Specifica il contenuto del file di output in linguaggio assembly.<br/><br/>Usare `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, usare `Fc`.<br/>**AssemblyCodeAndHex**, usare `Fx`.|
|**AssemblerOutputFile**|Parametro **stringa facoltativo.**<br/><br/>Specifica il nome per il file listato di codice dell'assembly.|
|**CompileD2DCustomEffect**|Parametro **bool** facoltativo.<br/><br/>Compila un effetto personalizzato Direct2D che contiene pixel shader. Non usare per un effetto personalizzato di vertex o compute shader.|
|**ConsumeExportFile**|Parametro **stringa facoltativo.**|
|**DisableOptimizations**|Parametro **bool** facoltativo.<br/><br/>Disabilita le ottimizzazioni.<br/><br/>`/Od` implica `/Gfp` anche se l'output può non essere identico a `/Od /Gfp`.|
|**EnableDebuggingInformation**|Parametro **bool** facoltativo.<br/><br/>Abilita le informazioni di debug.|
|**EnableUnboundedDescriptorTables**|Parametro **bool** facoltativo.<br/><br/>Informa il compilatore che uno shader può contenere una dichiarazione di una matrice di risorse con intervallo senza limiti. Disponibile per Modello shader 5.1 e versioni successive.<br/><br/>Usare `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Parametro **stringa facoltativo.**<br/><br/>Specifica il nome del punto di ingresso per lo shader.<br/><br/>Usare `/E[name]`.|
|**GenerateExportFile**|Parametro **stringa facoltativo.**|
|**GenerateExportShaderProfile**|Parametro **stringa facoltativo.**|
|**HeaderFileOutput**|Parametro **stringa facoltativo.**<br/><br/>Specifica un nome per il file di intestazione contenente il codice oggetto.<br/><br/>Usare `/Fh [name]`.|
|**ObjectFileOutput**|Parametro **stringa facoltativo.**<br/><br/>Specifica un nome per il file oggetto.<br/><br/>Usare `/Fo [name]`.|
|**PreprocessorDefinitions**|Parametro **string[]** facoltativo.<br/><br/>Definisce i simboli di pre-elaborazione per il file origine.|
|**SetRootSignature**|Parametro **stringa facoltativo.**<br/><br/>Associa la firma radice al bytecode dello shader. Disponibile per Modello shader 5.0 e versioni successive.<br/><br/>Usare `/setrootsignature`.|
|**ShaderModel**|Parametro **stringa facoltativo.**<br/><br/>Specifica il modello di shader. Alcuni tipi di shader possono essere usati solo con modelli di shader recenti.<br/><br/>Usare `/T [type]_[model]`.|
|**ShaderType**|Parametro **stringa facoltativo.**<br/><br/>Specifica il tipo di shader.<br/><br/>Usare `/T [type]_[model]`.<br/><br/>**Effect**, usare `fx`.<br/>**Vertex**, usare `vs`.<br/>**Pixel**, usare `ps`.<br/>**Geometry**, usare `gs`.<br/>**Hull**, usare `hs`.<br/>**Domain**, usare `ds`.<br/>**Compute**, usare `cs`.<br/>**Library**, usare `lib`.<br/>**RootSignature**, genera oggetto firma radice.|
|**Origine**|Parametro **ITaskItem** obbligatorio.|
|**SuppressStartupBanner**|Parametro **bool** facoltativo.<br/><br/>Evita la visualizzazione del messaggio di avvio e dei messaggi informativi.<br/><br/>Usare `/nologo`.|
|**TrackerLogDirectory**|Parametro **stringa facoltativo.**|
|**TreatWarningAsError**|Parametro **bool** facoltativo.<br/><br/>Considera tutti gli avvisi del compilatore come errori.<br/><br/>Per un nuovo progetto, potrebbe essere preferibile usare `/WX` in tutte le compilazioni. La risoluzione degli avvisi garantirà il minor numero possibile di errori del codice di difficile individuazione.|
|**VariableName**|Parametro **stringa facoltativo.**<br/><br/>Specifica un nome per la variabile nel file di intestazione.<br/><br/>Usare `/Vn [name]`.|

## <a name="see-also"></a>Vedi anche

[Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)