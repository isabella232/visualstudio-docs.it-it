---
title: Attività Error | Microsoft Docs
description: Usare l'MSBuild error per arrestare una compilazione e registrare un errore in base a un'istruzione condizionale valutata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ad3b206dbbbc65b2a3a08bc4bee7e8a4e4e85773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108967"
---
# <a name="error-task"></a>attività Error

Interrompe una compilazione e registra un errore in base a un'istruzione condizionale valutata.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Error` .

| Parametro | Descrizione |
|---------------| - |
| `Code` | Parametro `String` facoltativo.<br /><br /> Codice errore da associare all'errore. |
| `File` | Parametro `String` facoltativo.<br /><br /> Il nome del file che contiene l'errore. Se non viene indicato alcun nome file, verrà usato il file contenente l'attività di errore. |
| `HelpKeyword` | Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'errore. |
| `Text` | Parametro `String` facoltativo.<br /><br /> Testo dell'errore MSBuild log se `Condition` il parametro restituisce `true` . |

## <a name="remarks"></a>Commenti

`Error`L'attività consente MSBuild di generare testo di errore ai logger e di arrestare l'esecuzione della compilazione.

Se il parametro `Condition` restituisce `true`, la compilazione viene interrotta e viene registrato un errore. Se non esiste un parametro `Condition`, l'errore viene registrato e l'esecuzione della compilazione viene arrestata. Per altre informazioni sulla registrazione, vedere [Recupero dei log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

L'esempio di codice seguente verifica che siano impostate tutte le proprietà richieste. In caso contrario, il progetto genera un evento di errore e registra il valore del parametro `Text` sull'attività `Error`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
