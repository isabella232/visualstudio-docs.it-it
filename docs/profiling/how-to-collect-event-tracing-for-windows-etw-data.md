---
title: Raccogliere dati ETW (Event Tracing for Windows) | Microsoft Docs
description: Informazioni su come usare Event Tracing for Windows (ETW) per determinare dove si verificano problemi di prestazioni nell'applicazione. È possibile visualizzare i dati con VSPerfReport.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42de6efe72db8ae8cc1583114a288dd037c4b0c4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150469"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procedura: Raccogliere dati ETW (Event Tracing for Windows)

Event Tracing for Windows (ETW) è un'efficace funzionalità di traccia a livello di kernel che consente al profiler di registrare eventi definiti dall'applicazione o dal kernel. I dati raccolti dal provider di eventi possono essere visualizzati solo tramite l'opzione /**Summary:ETW** dello strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md). Questo rapporto può essere usato per determinare i punti nell'applicazione in cui si verificano problemi di prestazioni.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Per abilitare i provider di traccia eventi

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.

2. In **Pagine delle proprietà** fare clic sulle proprietà di **Eventi Windows**.

3. Dall'elenco **Selezionare i provider di traccia eventi per raccogliere dati da** selezionare i provider di eventi da usare per la profilatura dell'applicazione.

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
