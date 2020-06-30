---
title: Tabella di riferimento delle regole di prestazioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48659a0b5981d545a706abfcaa7c3db24052cd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548408"
---
# <a name="performance-rules-reference"></a>Tabella di riferimento delle regole di prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le regole di prestazioni degli strumenti di profilatura forniscono informazioni e avvisi aggiuntivi sulle prestazioni dell'applicazione. Le regole di prestazioni consentono di analizzare in un'esecuzione di profilatura i dati raccolti da origini quali i contatori delle prestazioni dei processori e di Windows. I messaggi relativi alle regole vengono visualizzati nella finestra di output degli errori dell'ambiente di sviluppo integrato di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. I messaggi sono elencati con uno dei livelli di regole seguenti:  
  
|Category|Descrizione|  
|-|-|  
|**Errore**|Poche regole generano messaggi di errore poiché la maggior parte dei problemi di prestazioni non sono effettivamente errori. Un messaggio di errore può indicare un errore nella raccolta dei dati di profilatura.|  
|**Avviso**|Gli avvisi indicano un'area dell'applicazione che potenzialmente può dare origine a problemi di prestazioni o che potrebbe essere ottimizzata.|  
|**Informazioni**|I messaggi di informazioni indicano che l'analisi di una condizione della regola non ha raggiunto la soglia per generare un messaggio di errore o che le informazioni nel messaggio sono utili ma non indicano un problema di prestazioni.|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Regole di prestazioni in base all'ID](../profiling/performance-rules-by-id.md)  
  
 Le regole di prestazioni degli strumenti di profilatura sono organizzate in quattro categorie:  
  
|Category|Descrizione|  
|-|-|  
|[Regole prestazioni .NET Framework utilizzo](../profiling/dotnet-framework-usage-performance-rules.md)|Regole che consentono di usare .NET Framework in modo efficiente.|  
|[Regole relative alle prestazioni di paging e memoria](../profiling/memory-and-paging-performance-rules.md)|Regole che analizzano il comportamento di paging e Managed Memory dell'applicazione.|  
|[Regole di utilizzo di Strumenti di profilatura](../profiling/profiling-tools-usage-rules.md)|Regole che permettono di usare gli strumenti di profilatura in modo efficiente.|  
|[Regole sulle prestazioni di monitoraggio delle risorse](../profiling/resource-monitoring-performance-rules.md)|Messaggi di informazioni sull'uso del processore e della memoria in un'esecuzione di profilatura.|
