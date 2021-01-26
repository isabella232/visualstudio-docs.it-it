---
title: Creare un report ETW degli strumenti di profilatura | Microsoft Docs
description: Informazioni su come creare un report di Event Tracing for Windows (ETW). Elenca gli eventi ETW registrati in una sessione di prestazioni Strumenti di profilatura di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c35a3e2d7da9472167c2ac20400fe3b3992b4883
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800479"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Procedura: Creare un report ETW degli strumenti di profilatura
Il report ETW (Event Tracing for Windows) elenca gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I dati ETW vengono raccolti in un file binario (.*ETL*). Per ulteriori informazioni su questo report, vedere il [report Event Tracing for Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Non è possibile visualizzare i report ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Per informazioni su come raccogliere dati ETW usando l'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , vedere [procedura: raccogliere dati di Event Tracing for Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Per informazioni su come raccogliere dati ETW da un prompt dei comandi, vedere [VSPerfCmd](../profiling/vsperfcmd.md) ed [Eventi](../profiling/events-vsperfcmd.md).

  Per generare il rapporto ETW, utilizzare il comando **VSReport/Summary: ETW** . Il. *ETL* che contiene i dati ETW deve trovarsi nella stessa directory dei dati di profilatura (.*VSP* o. *vsps*) file. Per impostazione predefinita, il report viene generato come file con valori delimitati da virgole, con estensione *csv*. Per altre informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Per generare un report ETW

- In una finestra del **prompt dei comandi** digitare la riga di comando seguente:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |Elemento|Descrizione|
    |-|-|
    |*ToolsPath*|Percorso dell'utilità degli strumenti di profilatura. Per altre informazioni, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|I dati di profilatura (.*VSP* o. *vsps*) file. Sono accettati percorsi completi e parziali.|
    |Xml|Genera un report in formato XML.|
