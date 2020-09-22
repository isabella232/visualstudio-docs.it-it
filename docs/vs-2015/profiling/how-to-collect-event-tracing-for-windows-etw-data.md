---
title: 'Procedura: Raccogliere dati ETW (Event Tracing for Windows) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839792"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procedura: Raccogliere dati ETW (Event Tracing for Windows)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Event Tracing for Windows (ETW) è un'efficace funzionalità di traccia a livello di kernel che consente al profiler di registrare eventi definiti dall'applicazione o dal kernel. I dati raccolti dal provider di eventi possono essere visualizzati solo tramite l'opzione /**Summary:ETW** dello strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md). Questo rapporto può essere usato per determinare i punti nell'applicazione in cui si verificano problemi di prestazioni.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app di Windows Store richiedono nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Per abilitare i provider di traccia eventi  
  
1. In **Esplora prestazioni**fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.  
  
2. In **Pagine delle proprietà** fare clic sulle proprietà di **Eventi Windows**.  
  
3. Dall'elenco **Selezionare i provider di traccia eventi per raccogliere dati da** selezionare i provider di eventi da usare per la profilatura dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
