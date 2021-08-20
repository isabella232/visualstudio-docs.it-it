---
title: Filtro delle visualizzazioni report | Microsoft Docs
description: In Visual Studio applicare filtri ai file di dati di profilatura per limitare i dati di profilatura visualizzati nelle visualizzazioni dei report di prestazioni ed esportati in file di report.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22ec32af90a67d40c4f753bf3c1aea3f3f0010b8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150378"
---
# <a name="filter-report-views"></a>Filtrare le visualizzazioni report
È possibile applicare filtri ai file di dati di profilatura per limitare i dati di profilatura che appaiono nelle visualizzazioni report Prestazioni e vengono esportati nei file di report. È possibile ridurre un report ai dati tra due valori di timestamp e ridurre i dati a processi e thread specifici. È possibile salvare i filtri in un file e quindi creare un filtro per un altro file di dati di profilatura importando il filtro salvato.

 È anche possibile limitare un report a un intervallo di tempo usando la sequenza temporale grafica della visualizzazione Riepilogo. Vedere [Procedura: Filtrare le visualizzazioni report dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Per escludere il codice di sistema e di terze parti da un report, vedere [Procedura: Filtrare visualizzazioni report degli strumenti per la profilatura per visualizzare Just My Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedure

#### <a name="to-create-a-profiler-report-filter"></a>Per creare un filtro report del profiler

1. Se non appare la finestra del filtro delle visualizzazioni dei report di prestazioni, fare clic su **Mostra filtro** nella barra degli strumenti della visualizzazione report Prestazioni.

     Il filtro della visualizzazione report Prestazioni è una tabella. Ogni riga della tabella rappresenta una clausola del filtro. È possibile aggiungere qualsiasi numero di clausole a un filtro.

2. Per ogni clausola da aggiungere a un filtro, selezionare o immettere i valori nei campi seguenti di una riga.

    |Campo|Descrizione|
    |-----------|-----------------|
    |**And/Or**|Scegliere **And** se questa clausola e la successiva devono essere entrambe vere (true) per restituire un risultato. Scegliere **Or** se questa clausola o la successiva può essere vera (true) per restituire un risultato.|
    |**Campo**|Selezionare il campo del report da usare nella clausola del filtro dall'elenco di campi dati visualizzato.|
    |**Operatore**|Selezionare l'operatore che specifica la relazione da impostare nella clausola tra il campo e il valore.<br /><br /> =    Uguale a<br /><br /> <>  Non uguale a<br /><br /> <    Minore di<br /><br /> >    Maggiore di<br /><br /> <=  Minore o uguale a<br /><br /> >=  Maggiore o uguale a|
    |**Valore**|Selezionare o immettere il valore da cercare. Per alcuni campi è presente l'elenco dei valori disponibili.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Per creare un filtro report del profiler dalla visualizzazione report Contrassegni

1. Selezionare **Contrassegni** dall'elenco **Visualizzazione corrente** nella barra degli strumenti della visualizzazione report Prestazioni.

    Viene visualizzato il report del profiler Contrassegni.

2. Selezionare l'ETW o il campionamento che si desidera utilizzare come punto iniziale del report.

3. Tenere premuto CTRL e fare clic sull'evento che si desidera utilizzare come punto finale del rapporto.

4. Fare clic con il pulsante destro del mouse e quindi scegliere una delle opzioni seguenti:

   - **Aggiungi filtro in contrassegni** crea clausole di filtro che usano la colonna Contrassegno come campo del filtro.

   - **Aggiungi filtro in timestamp** crea clausole di filtro che usano la colonna Timestamp in millisecondi come campo del filtro.

     Le due opzioni consentono di filtrare il file di dati corrente in corrispondenza degli stessi punti di inizio e di fine. Ogni opzione può essere ottimizzata se si esporta il filtro per l'uso in altri report.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Per caricare un filtro esistente da un file

1. Nella barra degli strumenti della visualizzazione report Prestazioni fare clic su **Importa filtro**.

     Viene visualizzata la finestra di dialogo **Carica filtro**.

2. Specificare il percorso e il nome del file del filtro (VSPF) da caricare.

#### <a name="to-execute-a-filter"></a>Per eseguire un filtro

- Nella barra degli strumenti della visualizzazione report Prestazioni fare clic su **Esegui filtro**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Per arrestare un filtro la cui esecuzione richiede troppo tempo

- Nella barra degli strumenti della visualizzazione report Prestazioni fare clic su **Arresta filtro**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Per rimuovere un filtro in una visualizzazione report

1. Eliminare le righe delle clausole nel filtro della visualizzazione report Prestazioni.

2. Nella barra degli strumenti della visualizzazione report Prestazioni fare clic su **Esegui filtro**.

#### <a name="to-save-a-filter-to-a-file"></a>Per salvare un filtro in un file

1. Nella barra degli strumenti della visualizzazione report Prestazioni fare clic su **Esporta filtro**.

     Viene visualizzata la finestra di dialogo **Salva filtro**.

2. Specificare il percorso e il nome del file del filtro (VSPF) da salvare.

## <a name="see-also"></a>Vedi anche
- [Personalizzazione delle visualizzazioni dei report sugli strumenti delle prestazioni](../profiling/customizing-performance-tools-report-views.md)
