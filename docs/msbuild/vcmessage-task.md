---
title: Attività VCMessage | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività VCMessage per registrare i messaggi di avviso e di errore durante una compilazione per i progetti C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046745"
---
# <a name="vcmessage-task"></a>attività VCMessage

Registra gli avvisi e i messaggi di errore durante una compilazione.

## <a name="remarks"></a>Commenti

 Questa attività consente di implementare MSBuild per i progetti C++ e non può essere chiamata dall'utente. Per altre informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage** .

|Parametro|Descrizione|
|---------------|-----------------|
|**Argomenti**|Parametro **stringa** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|
|**Tipo**|Parametro **stringa** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica "Warning" per generare un messaggio di avviso o "Error" per generare un messaggio di errore.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
