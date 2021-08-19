---
title: Attività WriteCodeFragment | Microsoft Docs
description: Informazioni su MSBuild'attività WriteCodeFragment per generare un file di codice temporaneo dal frammento di codice generato specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6bfd357776428a9fbf08f15e82b796bd0ca0195f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039904"
---
# <a name="writecodefragment-task"></a>Attività WriteCodeFragment

Genera un file di codice temporaneo usando il frammento di codice generato specificato. Non elimina il file.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `WriteCodeFragment` .

|Parametro|Descrizione|
|---------------|-----------------|
|`AssemblyAttributes`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Descrizione degli attributi da scrivere. Il valore dell'elemento `Include` è il nome completo del tipo dell'attributo, ad esempio, "System.AssemblyVersionAttribute".<br /><br /> Ogni tipo di metadati è la coppia nome-valore di un parametro, che deve essere di tipo `String`. Alcuni attributi consentono solo gli argomenti posizionali del costruttore. Tuttavia, è possibile usare tali argomenti in qualsiasi attributo. Per impostare gli attributi posizionali del costruttore, usare nomi di metadati simili a "_Parameter1","_Parameter2" e così via.<br /><br /> L'indice del parametro non può essere ignorato.|
|`Language`|Parametro `String` obbligatorio.<br /><br /> Specifica il linguaggio del codice da generare.<br /><br /> `Language` può essere qualsiasi linguaggio per cui è disponibile un CodeDOM, ad esempio "C#" o "VisualBasic". Il file generato avrà l'estensione predefinita per tale linguaggio.|
|`OutputDirectory`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica la cartella di destinazione per il codice generato, di solito la cartella intermedia.|
|`OutputFile`|Parametro di ouput facoltativo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Specifica il percorso del file generato. Se questo parametro viene impostato usando un nome di file, la cartella di destinazione viene anteposta al nome del file. Se viene impostato usando una radice, la cartella di destinazione viene ignorata.<br /><br /> Se questo parametro non viene impostato, il nome del file di output è la cartella di destinazione, un nome di file arbitrario e l'estensione del file predefinita per il linguaggio specificato.|

## <a name="remarks"></a>Commenti

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
