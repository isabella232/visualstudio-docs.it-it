---
title: Creare un report calltrace degli strumenti di profilatura | Microsoft Docs
description: Creare un report di traccia delle chiamate degli strumenti di prestazioni per visualizzare le informazioni di temporizzazione per le funzioni e per le funzioni chiamate dalle funzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 297ca895e9cc2f24dde9ce6e271c889d6d0543c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141871"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedura: Creare un report calltrace degli strumenti di profilatura
Il *report calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elenca le informazioni di intervallo per ogni punto di ingresso e di uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. I report calltrace sono disponibili per i dati di profilatura solo se sono stati raccolti con il metodo di strumentazione.

> [!NOTE]
> Non è possibile visualizzare i report calltrace in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È necessario usare lo strumento da riga di comando **VSPerfReport** per generare un file con valori delimitati da virgole con estensione *csv* o *xml*. Per altre informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Per creare un report calltrace

1. Aprire una **finestra del prompt dei** comandi.

2. Al prompt dei comandi digitare il comando seguente:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Elemento|Descrizione|
    |-|-|
    |*ToolsPath*|Percorso degli strumenti da riga di comando disponibili negli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Dati di profilatura (.*vsp* o . *vsps*) File. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|

## <a name="see-also"></a>Vedi anche
- [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)
