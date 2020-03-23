---
title: 'Procedura: Creare un report ETW degli strumenti di profilatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776401"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Procedura: Creare un report ETW degli strumenti di profilatura
Il report ETW (Event Tracing for Windows) elenca gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I dati ETW vengono raccolti in un file binario (.* etl*(). Per ulteriori informazioni su questo report, vedere [Report ETW (Event Tracing for Windows).](../profiling/event-tracing-for-windows-etw-report.md)

> [!NOTE]
> Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Per informazioni su come raccogliere dati ETW [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]utilizzando l'interfaccia per , vedere [Procedura: raccogliere dati ETW (Event Tracing for Windows).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Per informazioni su come raccogliere dati ETW da un prompt dei comandi, vedere [VSPerfCmd](../profiling/vsperfcmd.md) ed [Eventi](../profiling/events-vsperfcmd.md).

  Generare il report ETW utilizzando il comando **VSReport/summary:etw** . Le. *Etl* che contiene i dati ETW deve trovarsi nella stessa directory dei dati di profilatura (.* vsp* o . *vsps*) ﬁle. Per impostazione predefinita, il report viene generato come file con valori delimitati da virgole, con estensione *csv*. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Per generare un report ETW

- In una finestra del **prompt dei comandi** digitare la riga di comando seguente:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Percorso dell'utilità degli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*File VSP*|Dati di profilatura (.* vsp* o . *vsps*) ﬁle. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|
