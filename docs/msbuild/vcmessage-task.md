---
title: Attività VCMessage | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631211"
---
# <a name="vcmessage-task"></a>attività VCMessage

Registra gli avvisi e i messaggi di errore durante una compilazione.

## <a name="remarks"></a>Note

 Questa attività consente di implementare MSBuild C++ per i progetti e non può essere chiamata dall'utente. Per altre informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage**.

|Parametro|Descrizione|
|---------------|-----------------|
|**Argomenti**|Parametro **String** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|
|**Tipo**|Parametro **String** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica "Warning" per generare un messaggio di avviso o "Error" per generare un messaggio di errore.|

## <a name="see-also"></a>Vedere anche

- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
