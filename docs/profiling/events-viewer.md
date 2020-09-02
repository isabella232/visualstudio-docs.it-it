---
title: Visualizzatore eventi | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4cba043d8300d47ae5ffba1c175a19fcfa2e65ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330331"
---
# <a name="events-viewer"></a>Visualizzatore eventi

Il Visualizzatore eventi generici Mostra l'attività dell'app tramite un elenco di eventi come caricamento del modulo, avvio del thread e configurazione di sistema. Questa visualizzazione consente di diagnosticare meglio il funzionamento dell'app all'interno del profiler di Visual Studio.

## <a name="setup"></a>Configurazione

1. Selezionare **ALT + F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la casella di controllo **Visualizzatore eventi** .

   ![Casella di controllo Visualizzatore eventi selezionato](../profiling/media/eventsviewerselected.png "Casella di controllo Visualizzatore eventi selezionato")

1. Selezionare il pulsante **Avvia** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, esaminare lo scenario per profilare nell'app. Quindi selezionare **Arresta raccolta** o Chiudi l'app per visualizzare i dati.

   ![Finestra che mostra la raccolta di arresti](../profiling/media/stopcollectioneventsviewer.png "Finestra che mostra la raccolta di arresti")

Per ulteriori informazioni su come rendere più efficiente lo strumento, vedere [ottimizzazione delle impostazioni di profilatura](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Informazioni sui dati

![Traccia di un Visualizzatore eventi](../profiling/media/eventviewertrace.png "Traccia di un Visualizzatore eventi")

|Nome della colonna|Descrizione|
|----------|---------------------|
|Provider Name|Origine evento|
|Nome evento|Evento come specificato dal provider|
|Testo|Descrizioni del provider, il nome dell'evento e l'ID dell'evento|
|Timestamp (MS)|Quando è avvenuto l'evento|
|GUID del provider|ID del provider di eventi|
|ID evento|ID dell'evento.|
|ID di processo|Processo da cui si è verificato l'evento (se noto)|
|Process Name|Nome del processo se è in esecuzione attivamente|
|ID del thread|ID del thread da cui si è verificato l'evento (se noto)|

Se per impostazione predefinita manca una colonna, fare clic con il pulsante destro del mouse su una delle intestazioni di colonna esistenti e selezionare la colonna che si desidera aggiungere.

![Aggiunta di colonne al Visualizzatore eventi](../profiling/media/eventvieweraddcolumns.png "Aggiunta di colonne al Visualizzatore eventi")

Quando si seleziona un evento, viene visualizzata la finestra **proprietà aggiuntive** . **Proprietà comuni** Visualizza l'elenco delle proprietà che verranno visualizzate per qualsiasi evento. **Proprietà payload** Visualizza proprietà specifiche dell'evento. Per alcuni eventi, è anche possibile visualizzare gli **stack**.

![Visualizzatore eventi che Mostra gli stack](../profiling/media/eventviewerstacks.png "Visualizzatore eventi che Mostra gli stack")

## <a name="organize-your-data"></a>Organizzare i dati

Tutte le colonne ad eccezione della colonna di **testo** sono ordinabili.

![Traccia del Visualizzatore eventi](../profiling/media/eventviewertrace.png "Traccia del Visualizzatore eventi")

Il Visualizzatore eventi Visualizza fino a 20.000 eventi alla volta. Per concentrarsi sugli eventi di interesse, è possibile filtrare la visualizzazione degli eventi selezionando il filtro evento. È anche possibile vedere quale percentuale del numero totale di eventi si sono verificati per ogni provider. Passare il puntatore del mouse su un singolo filtro eventi per visualizzare una descrizione comando che mostra:

- Nome evento
- Provider
- GUID
- Percentuale di eventi totali
- Conteggio eventi

![Filtro eventi del Visualizzatore eventi](../profiling/media/eventviewereventfilter.png "Filtro eventi del Visualizzatore eventi")

Il filtro del provider Mostra la percentuale del numero totale di eventi che si sono verificati per ogni provider. Passare il puntatore del mouse su un singolo provider per visualizzare una descrizione comando simile con il nome del provider, la percentuale di eventi totali e il conteggio degli eventi.

![Filtro del provider del Visualizzatore eventi](../profiling/media/eventviewerproviderfilter.png "Filtro del provider del Visualizzatore eventi")
