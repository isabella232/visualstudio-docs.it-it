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
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547992"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedura: Creare un rapporto calltrace degli strumenti di profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il *report calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elenca le informazioni di intervallo per ogni punto di ingresso e di uscita delle funzioni dell'applicazione e ogni chiamata ad altre funzioni da parte di una determinata funzione. I report calltrace sono disponibili per i dati di profilatura solo se sono stati raccolti con il metodo di strumentazione.  
  
> [!NOTE]
> Non è possibile visualizzare i report calltrace in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. È necessario utilizzare lo strumento da riga di comando **VSPerfReport** per generare un file con valori delimitati da virgole (CSV) o XML. Per altre informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Per creare un report calltrace  
  
1. Aprire una finestra del **prompt dei comandi**.  
  
2. Al prompt dei comandi digitare il comando seguente:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |Elemento Command|Descrizione|
    |-|-|  
    |*ToolsPath*|Percorso degli strumenti da riga di comando degli strumenti di profilatura. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|File (con estensione vsp o vsps) dei dati di profilatura. Sono accettati percorsi completi e parziali.|  
    |Xml|Genera un report in formato XML.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: raccogliere dati di Event Tracing for Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API per strumenti di profilatura](../profiling/profiling-tools-apis.md)
