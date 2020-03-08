---
title: Attività Message | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865362"
---
# <a name="message-task"></a>attività Message

Registra un messaggio durante una compilazione.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `Message`.

|Parametro|Descrizione|
|---------------|-----------------|
|`Importance`|Parametro `String` facoltativo.<br /><br /> Specifica l'importanza del messaggio. Il valore di questo parametro può essere `high`, `normal` o `low`. Il valore predefinito è `normal`.|
|`Text`|Parametro `String` facoltativo.<br /><br /> Testo dell'errore da registrare.|

## <a name="remarks"></a>Osservazioni

 Il `Message` attività consente ai progetti MSBuild di emettere messaggi ai logger in diversi passaggi del processo di compilazione.

 Se il parametro `Condition` restituisce `true`, verrà registrato il valore del parametro `Text` e la compilazione continuerà a essere eseguita. Se il parametro `Condition` non esiste, verrà registrato il testo del messaggio. Per altre informazioni sulla registrazione, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

 Per impostazione predefinita, il messaggio viene inviato a tutti i logger registrati. Il parametro `Importance` viene interpretato dal logger. Un messaggio impostato su `high` viene in genere inviato quando il livello di dettaglio del logger è impostato su <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Minimal` o successiva. Un messaggio impostato su `low` viene inviato quando il livello di dettaglio del logger è impostato su <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Detailed`.

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 Nell'esempio di codice riportato di seguito i messaggi vengono registrati in tutti i logger registrati.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
