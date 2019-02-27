---
title: 'Procedura: Creare un report ETW degli strumenti di profilatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 310c43ea4dbdf1f50a76b574ec52baa589769034
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614467"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Procedura: Creare un report ETW degli strumenti di profilatura
Il report ETW (Event Tracing for Windows) elenca gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I dati ETW vengono raccolti in un file binario con estensione *etl*. Per altre informazioni sul report, vedere [Report Event Tracing for Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
>  Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Per informazioni su come raccogliere dati ETW usando l'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Procedura: Raccogliere dati ETW (Event Tracing for Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Per informazioni su come raccogliere dati ETW da un prompt dei comandi, vedere [VSPerfCmd](../profiling/vsperfcmd.md) ed [Eventi](../profiling/events-vsperfcmd.md).

  Per generare il report ETW, usare il comando **VSReport/summary:etw**. Il file con estensione *etl* contenente i dati ETW deve trovarsi nella stessa directory del file dei dati di profilatura, con estensione *vsp* o *vsps*. Per impostazione predefinita, il report viene generato come file con valori delimitati da virgole, con estensione *csv*. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Per generare un report ETW

-   In una finestra del **prompt dei comandi** digitare la riga di comando seguente:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Percorso dell'utilità degli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|File con estensione *vsp* o *vsps* dei dati di profilatura. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|
