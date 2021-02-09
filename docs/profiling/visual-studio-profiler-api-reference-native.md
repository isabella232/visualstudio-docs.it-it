---
title: Riferimenti per le API del profiler di Visual Studio (native)
description: Informazioni sul modo in cui le API del profiler di Visual Studio consentono di controllare a livello di codice la quantità di dati raccolti e di inserire i timestamp e i contrassegni di profilo durante la profilatura.
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
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9d8fe6f4f1f38277a8cf317fa55fbc883b85394a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890539"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Riferimenti per le API del profiler di Visual Studio (native)
Le API del profiler di Visual Studio consentono di controllare a livello di codice la quantità di dati raccolti e di inserire contrassegni sia per il timestamp che per il profilo durante la profilatura. Per usare le API native, è necessario includere il file di intestazione *VSPerf. h* e aggiungere *VSPerf. lib* nel progetto.

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
