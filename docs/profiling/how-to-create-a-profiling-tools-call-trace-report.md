---
title: 'Procedura: Creare un report calltrace degli strumenti di profilatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b184310d837193679a1a5eacf2fbae4ecf29caa
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778986"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedura: Creare un report calltrace degli strumenti di profilatura
Il *report calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elenca le informazioni di intervallo per ogni punto di ingresso e di uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. I report calltrace sono disponibili per i dati di profilatura solo se sono stati raccolti con il metodo di strumentazione.

> [!NOTE]
> Non è possibile visualizzare i report calltrace in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È necessario usare lo strumento da riga di comando **VSPerfReport** per generare un file con valori delimitati da virgole con estensione *csv* o *xml*. Per altre informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Per creare un report calltrace

1. Aprire una finestra **Prompt dei comandi**.

2. Al prompt dei comandi digitare quanto segue:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Percorso degli strumenti da riga di comando disponibili negli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|File con estensione *vsp* o *vsps* dei dati di profilatura. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|

## <a name="see-also"></a>Vedere anche
- [Procedura: raccogliere dati di Event Tracing for Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)
