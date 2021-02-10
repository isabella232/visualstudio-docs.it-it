---
title: Salvataggio ed esportazione dei dati degli strumenti per le prestazioni | Microsoft Docs
description: Informazioni su come salvare le visualizzazioni filtrate o non filtrate dei file di dati di profilatura (con estensione vsp) come file di report analizzati (con estensione vsps).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa43d324f23958c9dc9b72447527ecd035e99c53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950104"
---
# <a name="save-and-export-performance-tools-data"></a>Salvare ed esportare i dati degli strumenti per le prestazioni
Questo articolo descrive come salvare ed esportare i file di dati sulle prestazioni.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Procedura: Salvare i file di dati sulle prestazioni come file di report analizzati
 È possibile salvare le visualizzazioni filtrate o non filtrate dei dati di profilatura (.** con estensione vsp) come report analizzato (.*file vsps*). Un file di report analizzato può essere visualizzato nella finestra di visualizzazione report ed è significativamente più piccolo dell'originale. file *VSP* . Tuttavia, non è possibile applicare un filtro ai dati di un oggetto. file *vsps* . È possibile creare un file di report analizzato dalla Esplora prestazioni senza aprire il file nell'Integrated Development Environment (IDE) oppure è possibile aprire e filtrare il. file *VSP* e quindi salvare i risultati.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Per salvare un report di prestazioni analizzato da Esplora prestazioni

1. In **Report** fare clic con il pulsante destro sul file dei dati di profilatura da analizzare e quindi fare clic su **Salva dati analizzati**.

2. Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.

3. Fare clic su **Salva**.

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Per salvare un report di prestazioni analizzato dalla finestra di visualizzazione report

1. Aprire i dati di profilatura (.*VSP*) nella finestra di visualizzazione report.

2. (Facoltativo) Applicare un filtro ai dati. Per ulteriori informazioni, vedere [filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).

3. Fare clic su **Salva dati analizzati** nella barra degli strumenti della finestra di visualizzazione report.

4. Nella finestra di dialogo **Salva dati analizzati** specificare la directory e quindi digitare il nome del file.

5. Fare clic su **Salva**.

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Procedura: Esportare i report degli strumenti di profilatura in un file con estensione xml o csv
 È possibile esportare una o più visualizzazioni report da un. file *VSP* o. *vsps* il file di dati di profilatura come un file delimitato da virgole o XML. Filtrare i dati nella finestra di visualizzazione report prima dell'esportazione o esportare le visualizzazioni di report dell'intero file di dati dalla finestra **Esplora prestazioni** .

> [!NOTE]
> È anche possibile copiare e incollare le righe selezionate dalla finestra di visualizzazione report come valori separati da tabulazioni.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Per esportare un report di prestazioni analizzato dalla finestra Esplora prestazioni

1. In **Esplora prestazioni** selezionare il report e quindi fare clic con il pulsante destro del mouse e selezionare **Esporta**.

     Viene visualizzata la finestra di dialogo **Esporta report** .

2. Selezionare le visualizzazioni di report da esportare.

3. In **Utilizzare nei rapporti il prefisso** specificare il prefisso da aggiungere al nome del report.

4. In **Percorso rapporto esportato** specificare la directory.

5. In **Formato del rapporto esportato** selezionare (Delimitato da virgole) \*.csv\), o Dati XML (\*.xml\).

6. Fare clic su **esportare**.

     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefix> _ \<report view name> .\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Per esportare i report di prestazioni dalla finestra di visualizzazione report

1. Aprire. file *VSP* nella finestra di visualizzazione report.

2. (Facoltativo) Applicare un filtro ai dati. Per ulteriori informazioni, vedere [filtro delle visualizzazioni dei report di prestazioni](../profiling/performance-report-view-filter.md).

3. Fare clic su **Esporta report** nella barra degli strumenti della finestra di visualizzazione report.

4. Selezionare le visualizzazioni di report da esportare.

5. In **Utilizzare nei rapporti il prefisso** specificare il prefisso da aggiungere al nome del report.

6. In **Percorso rapporto esportato** specificare la directory.

7. In **formato report esportato** selezionare (delimitato da virgole) ( \* CSV) o dati XML ( \* . Xml).

8. Fare clic su **esportare**.

     Ogni visualizzazione del report viene salvata in un file separato denominato \<prefix> _ \<report view name> .\<csv&#124;xml>

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
- [Analizzare i dati degli strumenti per le prestazioni](../profiling/analyzing-performance-tools-data.md)
- [Confrontare i file di dati delle prestazioni](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
