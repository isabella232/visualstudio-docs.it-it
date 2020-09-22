---
title: Salvataggio ed esportazione dei dati degli strumenti per le prestazioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be6d5d732e5cbb2050c68ac8c7db722c3f709f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839512"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Salvataggio ed esportazione dei dati degli strumenti per le prestazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento descrive come salvare ed esportare i file di dati delle prestazioni.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a><a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Procedura: salvare i file di dati delle prestazioni come file di report analizzati  
 È possibile salvare le visualizzazioni filtrate o non filtrate dei file di dati di profilatura (estensione vsp) come file di report analizzato (estensione vsps). Un file di report analizzato può essere visualizzato nella finestra di visualizzazione report ed è notevolmente più piccolo del file con estensione vsp originale. Non è possibile tuttavia applicare un filtro ai dati di un file con estensione vsps. È possibile creare un file di report analizzato da Esplora prestazioni senza aprire il file nell'ambiente di sviluppo integrato (IDE) oppure è possibile aprire e filtrare il file con estensione vsp e quindi salvare i risultati.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Per salvare un report di prestazioni analizzato da Esplora prestazioni  
  
1. In **Report**fare clic con il pulsante destro sul file dei dati di profilatura da analizzare e quindi fare clic su **Salva dati analizzati**.  
  
2. Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
3. Fare clic su **Salva**.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Per salvare un report di prestazioni analizzato dalla finestra di visualizzazione report  
  
1. Aprire il file di dati di profilatura (con estensione vsp) nella finestra di Visualizzazione report.  
  
2. (Facoltativo) Applicare un filtro ai dati. Per ulteriori informazioni, vedere [filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).  
  
3. Fare clic su **Salva dati analizzati** nella barra degli strumenti della finestra di visualizzazione report.  
  
4. Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
5. Fare clic su **Salva**.  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Procedura: esportare i report degli strumenti per la profilatura in un file con estensione Xml o Csv  
 È possibile esportare una o più visualizzazioni di report da un file di dati di profilatura con estensione vsp o vsps come file delimitato da virgole o file XML. Filtrare i dati nella finestra di visualizzazione report prima dell'esportazione o esportare le visualizzazioni di report dell'intero file di dati dalla finestra **Esplora prestazioni** .  
  
> [!NOTE]
> È anche possibile copiare e incollare le righe selezionate dalla finestra di visualizzazione report come valori separati da tabulazioni.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Per esportare un report di prestazioni analizzato dalla finestra Esplora prestazioni  
  
1. In **Esplora prestazioni**selezionare il report e quindi fare clic con il pulsante destro del mouse e selezionare **Esporta**.  
  
     Viene visualizzata la finestra di dialogo **Esporta report** .  
  
2. Selezionare le visualizzazioni di report da esportare.  
  
3. In **Utilizzare nei rapporti il prefisso**specificare il prefisso da aggiungere al nome del report.  
  
4. In **Percorso rapporto esportato**specificare la directory.  
  
5. In **formato report esportato**selezionare (delimitato da virgole) (*. csv) o dati XML ( \* . Xml).  
  
6. Fare clic su **esportare**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefix> _ \<report view name> .\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Per esportare i report di prestazioni dalla finestra di visualizzazione report  
  
1. Aprire il file con estensione vsp nella finestra di visualizzazione report.  
  
2. (Facoltativo) Applicare un filtro ai dati. Per ulteriori informazioni, vedere [filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).  
  
3. Fare clic su **Esporta report** nella barra degli strumenti della finestra di visualizzazione report.  
  
4. Selezionare le visualizzazioni di report da esportare.  
  
5. In **Utilizzare nei rapporti il prefisso**specificare il prefisso da aggiungere al nome del report.  
  
6. In **Percorso rapporto esportato**specificare la directory.  
  
7. In **formato report esportato**selezionare (delimitato da virgole) (*. csv) o dati XML ( \* . Xml).  
  
8. Fare clic su **esportare**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefix> _ \<report view name> .\<csv&#124;xml>  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)   
 [Analisi dei dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)   
 [Confronto tra file di dati delle prestazioni](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
