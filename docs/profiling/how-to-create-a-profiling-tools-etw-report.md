---
title: Creare un report ETW degli strumenti di profilatura | Microsoft Docs
description: Informazioni su come creare un report Event Tracing for Windows (ETW). Elenca gli eventi ETW registrati in una sessione Visual Studio Strumenti di profilatura prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 687e813b449f469386d1c2fce9a7b79ae7467497
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150235"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Procedura: Creare un report ETW degli strumenti di profilatura
Il report ETW (Event Tracing for Windows) elenca gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I dati ETW vengono raccolti in un file binario (.*etl*) file. Per altre informazioni su questo report, vedere [Event Tracing for Windows (ETW) report](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Per informazioni su come raccogliere dati ETW usando l'interfaccia per , vedere Procedura: Raccogliere dati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [ETW (Event Tracing for Windows).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Per informazioni su come raccogliere dati ETW da un prompt dei comandi, vedere [VSPerfCmd](../profiling/vsperfcmd.md) ed [Eventi](../profiling/events-vsperfcmd.md).

  Per generare il report ETW, usare il **comando VSReport/summary:etw.** Le. *etl* che contiene i dati ETW deve essere nella stessa directory dei dati di profilatura (.*vsp* o . *vsps*) File. Per impostazione predefinita, il report viene generato come file con valori delimitati da virgole, con estensione *csv*. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Per generare un report ETW

- In una finestra del **prompt dei comandi** digitare la riga di comando seguente:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |Elemento|Descrizione|
    |-|-|
    |*ToolsPath*|Percorso dell'utilità degli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Dati di profilatura (.*vsp* o . *vsps*) File. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|
