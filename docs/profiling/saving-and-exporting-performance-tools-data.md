---
title: Salvataggio ed esportazione dei dati degli strumenti per le prestazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bb2020ff396eef3dd9dad4c0ed2e2fd015e0fd6
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "53838372"
---
# <a name="save-and-export-performance-tools-data"></a>Salvare ed esportare i dati degli strumenti per le prestazioni
Questo articolo descrive come salvare ed esportare i file di dati sulle prestazioni.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Procedura: Salvare i file di dati sulle prestazioni come file di report analizzati  
 È possibile salvare visualizzazioni filtrate o non filtrate dei file di dati di profilatura (con estensione *vsp*) come file di report analizzati (con estensione *vsps*). Un file di report analizzato può essere visualizzato nella finestra di visualizzazione report e ha dimensioni decisamente inferiori rispetto al file con estensione *vsp* originale. Non è possibile, tuttavia, applicare un filtro ai dati di un file con estensione *vsps*. È possibile creare un file di report analizzato da Esplora prestazioni senza aprire il file nell'ambiente di sviluppo integrato (IDE) oppure è possibile aprire e filtrare il file con estensione *vsp* e quindi salvare i risultati.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Per salvare un report di prestazioni analizzato da Esplora prestazioni  
  
1.  In **Report**fare clic con il pulsante destro sul file dei dati di profilatura da analizzare e quindi fare clic su **Salva dati analizzati**.  
  
2.  Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
3.  Fare clic su **Salva**.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Per salvare un report di prestazioni analizzato dalla finestra di visualizzazione report  
  
1.  Aprire il file di dati di profilatura (con estensione *vsp*) nella finestra di visualizzazione report.  
  
2.  (Facoltativo) Applicare un filtro ai dati. Per altre informazioni, vedere [Filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).  
  
3.  Fare clic su **Salva dati analizzati** nella barra degli strumenti della finestra di visualizzazione report.  
  
4.  Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.  
  
5.  Fare clic su **Salva**.  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Procedura: Esportare i report degli strumenti di profilatura in un file con estensione xml o csv  
 È possibile esportare una o più visualizzazioni di report da un file con estensione *vsp* o da un file di dati di profilatura con estensione *vsps* come file con valori delimitati da virgole o XML. Filtrare i dati nella finestra di visualizzazione report prima dell'esportazione o esportare le visualizzazioni di report dell'intero file di dati dalla finestra **Esplora prestazioni** .  
  
> [!NOTE]
>  È anche possibile copiare e incollare le righe selezionate dalla finestra di visualizzazione report come valori separati da tabulazioni.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Per esportare un report di prestazioni analizzato dalla finestra Esplora prestazioni  
  
1.  In **Esplora prestazioni**selezionare il report e quindi fare clic con il pulsante destro del mouse e selezionare **Esporta**.  
  
     Viene visualizzata la finestra di dialogo **Esporta report** .  
  
2.  Selezionare le visualizzazioni di report da esportare.  
  
3.  In **Utilizzare nei rapporti il prefisso**specificare il prefisso da aggiungere al nome del report.  
  
4.  In **Percorso rapporto esportato**specificare la directory.  
  
5.  In **Formato del rapporto esportato** selezionare (Delimitato da virgole) \*.csv\), o Dati XML (\*.xml\).  
  
6.  Fare clic su **Esporta**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefisso>_\<nome visualizzazione report>.\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Per esportare i report di prestazioni dalla finestra di visualizzazione report  
  
1.  Aprire il file con estensione *vsp* nella finestra di visualizzazione report.  
  
2.  (Facoltativo) Applicare un filtro ai dati. Per altre informazioni, vedere [Filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).  
  
3.  Fare clic su **Esporta report** nella barra degli strumenti della finestra di visualizzazione report.  
  
4.  Selezionare le visualizzazioni di report da esportare.  
  
5.  In **Utilizzare nei rapporti il prefisso**specificare il prefisso da aggiungere al nome del report.  
  
6.  In **Percorso rapporto esportato**specificare la directory.  
  
7.  In **Formato del rapporto esportato**, selezionare (Delimitato da virgole) (\*.csv) o Dati XML (\*.xml).  
  
8.  Fare clic su **Esporta**.  
  
     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefisso>_\<nome visualizzazione report>.\<csv&#124;xml>  
  
## <a name="see-also"></a>Vedere anche  
 [Esplora prestazioni](../profiling/performance-explorer.md)   
 [Analizzare i dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)   
 [Confrontare i file di dati delle prestazioni](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
