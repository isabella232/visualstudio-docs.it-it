---
title: 'Procedura: Creare un report calltrace degli strumenti di profilatura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03c039d0059e3e5768681ece9bb547b0f4eb7783
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432754"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedura: Creare un profilo rapporto calltrace degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il *report calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elenca le informazioni di intervallo per ogni punto di ingresso e di uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. I report calltrace sono disponibili per i dati di profilatura solo se sono stati raccolti con il metodo di strumentazione.  
  
> [!NOTE]
> Non è possibile visualizzare i report calltrace in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È necessario usare lo strumento da riga di comando **VSPerfReport** per generare un file con valori delimitati da virgole (file con estensione csv) o un file XML. Per altre informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Per creare un report calltrace  
  
1. Aprire una finestra del **prompt dei comandi**.  
  
2. Al prompt dei comandi digitare il seguente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Percorso degli strumenti da riga di comando degli strumenti di profilatura. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|File (con estensione vsp o vsps) dei dati di profilatura. Sono accettati percorsi completi e parziali.|  
    |Xml|Genera un report in formato XML.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Raccogliere Event Tracing for Windows (ETW) Data](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API degli strumenti di profilatura](../profiling/profiling-tools-apis.md)
