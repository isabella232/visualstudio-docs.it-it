---
title: Attività VCMessage | Microsoft Docs
description: Informazioni su MSBuild'attività VCMessage per registrare messaggi di avviso e di errore durante una compilazione per progetti C++.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 705298bf73bceda32ca82a9dc85f96816794d8e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108213"
---
# <a name="vcmessage-task"></a>attività VCMessage

Registra gli avvisi e i messaggi di errore durante una compilazione.

## <a name="remarks"></a>Commenti

 Questa attività consente di implementare MSBuild per i progetti C++ e non deve essere chiamata dall'utente. Per altre informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **VCMessage**.

|Parametro|Descrizione|
|---------------|-----------------|
|**Argomenti**|Parametro **String** facoltativo.<br /><br /> Elenco delimitato da punto e virgola dei messaggi da visualizzare.|
|**Codice**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|
|**Tipo**|Parametro **String** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare. Specifica "Warning" per generare un messaggio di avviso o "Error" per generare un messaggio di errore.|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
