---
title: Creazione di file dei dati di profilatura portabili tramite la riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 314dc97e5881949ee69131576932db1865969b2c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541041"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Creazione di file dei dati di profilatura portabili tramite la riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione di profilatura di file di dati portabili dalla riga di comando](https://docs.microsoft.com/visualstudio/profiling/creating-portable-profiling-data-files-from-the-command-line).  
  
Per semplificare la condivisione dei dati di profilatura è possibile usare lo strumento della riga di comando [VSPerfReport](../profiling/vsperfreport.md) per incorporare i simboli di un'esecuzione della profilatura nel file con estensione vsp.  
  
 È anche possibile creare un file di dati di profilatura preanalizzati (con estensione vsps), più piccolo e più facile da caricare nell'IDE.  
  
> [!NOTE]
>  Verificare che i file di simboli (con estensione pdb) siano disponibili per **VSPerfReport**. Per altre informazioni, vedere [Procedura: Specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Per altre informazioni sul percorso di **VSReport**, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Non è possibile filtrare i dati di profilatura di un file con estensione vsps.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Per incorporare i simboli per un'esecuzione della profilatura in un file di dati di profilatura (con estensione vsp)  
  
-   In una finestra del prompt dei comandi, digitare il comando seguente:  
  
     \<percorso>**VSPerfReport \<** file VSP> **/PackSymbols**  
  
     Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Per creare un file di riepilogo dati di profilatura  
  
-   In una finestra del prompt dei comandi, digitare il comando seguente:  
  
     \<percorso>**VSPerfReport \<** file VSP> **/SummaryFile** [**/Output:**\<nome file>]  
  
     Per impostazione predefinita il file con estensione vsps è denominato con il nome base del file con estensione vsp. È possibile specificare un nome alternativo con l'opzione **Output**.



