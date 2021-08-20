---
title: Report Traccia eventi per Windows (ETW) | Microsoft Docs
description: Leggere il report Event Tracing for Windows (ETW), che elenca gli eventi ETW registrati in una sessione di prestazioni di Visual Studio Strumenti di profilatura.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 76749460a68c70856c735ef6ae344188d58a5efc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061129"
---
# <a name="event-tracing-for-windows-etw-report"></a>Report Traccia eventi per Windows (ETW)
Il report Traccia eventi per Windows (ETW) indica gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I dati ETW vengono raccolti in un file binario (.*etl*) file.

> [!NOTE]
> Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Per informazioni su come raccogliere dati ETW usando l'Strumenti di profilatura dall'interfaccia , vedere Procedura: Raccogliere dati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [ETW (Event Tracing for Windows).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Per informazioni su come raccogliere dati ETW usando gli strumenti della riga di comando di [VSPerfCmd](../profiling/vsperfcmd.md), vedere [Eventi](../profiling/events-vsperfcmd.md).

- Per generare il report ETW, usare il comando **VSReport/Summary:ETW**. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

|Colonna|Descrizione|
|------------|-----------------|
|**Timestamp**|Identifica il momento in cui si è verificato l'evento.|
|**ID processo**|Identifica il processo che ha generato l'evento.|
|**Thread ID**|Identifica il thread che ha generato l'evento.|
|**Descrizione**|Identifica il provider di eventi.|
|**Tipo**|Identifica il tipo di evento.|
|**Proprietà**|Le proprietà dell'evento. Ogni evento è una coppia nome-valore separata da virgola e racchiusa tra parentesi.|
