---
title: Riferimenti per le API del profiler di Visual Studio (native)
description: Informazioni su come le API Visual Studio profiler consentono di controllare a livello di codice la quantità di dati raccolti e di inserire contrassegni di profilo e timestamp durante la profilatura.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 74e8637426cfec88ceecc5c60a2ab326957b29d9d57c0bb22ec71045b5996001
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368110"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Riferimenti per le API del profiler di Visual Studio (native)
Le API del profiler di Visual Studio consentono di controllare a livello di codice la quantità di dati raccolti e di inserire contrassegni sia per il timestamp che per il profilo durante la profilatura. Per usare le API native, includere il file di intestazione *VSPerf.h* e aggiungere *vsPerf.lib* nel progetto.

> [!NOTE]
> Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="in-this-section"></a>Contenuto della sezione
[CommentMarkAtProfile](../profiling/commentmarkatprofile.md)

[CommentMarkProfile](../profiling/commentmarkprofile.md)

[MarkProfile](../profiling/markprofile.md)

[NameProfile](../profiling/nameprofile.md)

[ResumeProfile](../profiling/resumeprofile.md)

[StartProfile](../profiling/startprofile.md)

[StopProfile](../profiling/stopprofile.md)

[SuspendProfile](../profiling/suspendprofile.md)

[PROFILE_CURRENTID](../profiling/profile-currentid.md)

## <a name="see-also"></a>Vedi anche

- [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)
- [Procedura dettagliata: Uso delle API del profiler](../profiling/walkthrough-using-profiler-apis.md)
