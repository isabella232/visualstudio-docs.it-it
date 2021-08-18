---
title: SDK del visualizzatore di concorrenza | Microsoft Docs
description: Informazioni su come usare l'SDK del visualizzatore di concorrenza per instrumentare il codice per visualizzare i marcatori. I marcatori sono icone visualizzate nel visualizzatore di concorrenza per contrassegnare gli eventi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c3d1cc162cc48cef6ee6e9fc1269ea262f5ff0a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039579"
---
# <a name="concurrency-visualizer-sdk"></a>SDK del visualizzatore di concorrenza
Con l'SDK del visualizzatore di concorrenza è possibile instrumentare il codice sorgente in modo che nel visualizzatore di concorrenza siano visualizzate informazioni aggiuntive. È possibile associare i dati aggiuntivi a fasi ed eventi nel codice. Queste visualizzazioni aggiuntive sono note come *marcatori*.  Per una procedura dettagliata introduttiva, vedere [Introducing the Concurrency Visualizer SDK](/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk).(Introduzione all'SDK del visualizzatore di concorrenza).

## <a name="properties"></a>Proprietà
 Flag, span e messaggi hanno due proprietà: categoria e importanza. Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) è possibile usare queste proprietà per filtrare il set di marcatori visualizzati. Queste proprietà influiscono anche sulla rappresentazione visiva dei marcatori. Ad esempio, l'importanza è rappresentata dalla dimensione dei flag, mentre il colore viene usato per indicare la categoria.

## <a name="basic-usage"></a>Uso di base
 Il visualizzatore di concorrenza espone un provider predefinito che è possibile usare per generare i marcatori. Il provider è già registrato nel visualizzatore di concorrenza e non è necessario eseguire altre operazioni per visualizzare i marcatori nell'interfaccia utente.

### <a name="c-and-visual-basic"></a>C# e Visual Basic
 In C#, Visual Basic e altro codice gestito usare il provider predefinito chiamando i metodi nella classe [Markers](/previous-versions/hh694099(v=vs.140)). Espone quattro metodi per la generazione di marcatori: [WriteFlag,](/previous-versions/hh694185%28v%3dvs.140%29) [EnterSpan,](/previous-versions/hh694205(v=vs.140)) [WriteMessage](/previous-versions/hh694161(v=vs.140))e [WriteAlert.](/previous-versions/hh694180(v=vs.140)) Sono disponibili più overload per queste funzioni, a seconda che si voglia o meno usare le impostazioni predefinite per le proprietà.  L'overload più semplice accetta solo un parametro di stringa che specifica la descrizione dell'evento. La descrizione viene visualizzata nei rapporti del visualizzatore di concorrenza.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Per aggiungere un SDK a un progetto C# o Visual Basic

1. Nella barra dei menu scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.

2. Scegliere il progetto in cui si vuole aggiungere l'SDK e selezionare il pulsante **Aggiungi SDK al progetto selezionato**.

3. Aggiungere un'istruzione imports o using al codice.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 In C++ creare un oggetto [classe marker_series](../profiling/marker-series-class.md) e usarlo per chiamare le funzioni.  La classe `marker_series` espone tre funzioni per la generazione di indicatori: [marker_series::write_flag Method](../profiling/marker-series-write-flag-method.md), [marker_series::write_message Method](../profiling/marker-series-write-message-method.md) e [marker_series::write_alert Method](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Per aggiungere un SDK a un progetto C++ o C

1. Nella barra dei menu scegliere **Analizza**, **Visualizzatore di concorrenza**, **Aggiungi SDK al progetto**.

2. Scegliere il progetto in cui si vuole aggiungere l'SDK e selezionare il pulsante **Aggiungi SDK al progetto selezionato**.

3. Per C++, includere `cvmarkersobj.h`. Per C, includere `cvmarkers.h`.

4. Aggiungere un'istruzione using al codice.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Creare un oggetto `marker_series` e passarlo al costruttore `span`.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Utilizzo personalizzato
 Per gli scenari avanzati, l'SDK del visualizzatore di concorrenza espone maggiore controllo.  A scenari più avanzati sono associati due concetti principali: provider marcatori e serie di marcatori. I provider marcatori sono provider ETW diversi, ognuno dei quali ha un GUID specifico. Le serie di marcatori sono canali di eventi seriali generati da un provider, che possono essere usate per organizzare gli eventi generati da un provider marcatori.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Per usare un nuovo provider marcatori in un progetto C# o Visual Basic

1. Creare un oggetto [MarkerWriter](/previous-versions/hh694138(v=vs.140)).  Il costruttore accetta un GUID.

2. Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) del visualizzatore di concorrenza.  Selezionare la scheda **Marcatori** e selezionare il pulsante **Aggiungi nuovo provider**. Nella finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) immettere il GUID usato per creare il provider e una descrizione del provider.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Per usare un nuovo provider marcatori in un progetto C++ o C

1. Usare la funzione `CvInitProvider` per inizializzare un PCV_PROVIDER.  Il costruttore accetta un GUID\* e PCV_PROVIDER\*.

2. Per registrare il provider, aprire la finestra di dialogo [Impostazioni avanzate](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Selezionare la scheda **Marcatori** e selezionare il pulsante **Aggiungi nuovo provider**. Nella finestra di dialogo immettere il GUID usato per creare il provider e una descrizione del provider.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Per usare una serie di marcatori in un progetto C# o Visual Basic

1. Per usare un nuovo oggetto [MarkerSeries](/previous-versions/hh694127(v=vs.140)), è necessario prima crearlo tramite un oggetto [MarkerWriter](/previous-versions/hh694138(v=vs.140)). A questo punto è possibile generare gli eventi marcatori direttamente dalla nuova serie.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Per usare una serie di marcatori in un progetto C++

1. Creare un oggetto `marker_series`.  Gli eventi possono essere generati da questa serie nuova.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>Per usare una serie di marcatori in un progetto C

1. Usare la funzione `CvCreateMarkerSeries` per creare PCV_MARKERSERIES.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Vedi anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Informazioni di riferimento sulla libreria C++](../profiling/cpp-library-reference.md)|Viene descritta l'API del visualizzatore di concorrenza per C++.|
|[Informazioni di riferimento sulla libreria C](../profiling/c-library-reference.md)|Viene descritta l'API del visualizzatore di concorrenza per C.|
|[Strumentazione](/previous-versions/hh694104(v=vs.140))|Viene descritta l'API del visualizzatore di concorrenza per il codice gestito.|
|[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)|Informazioni di riferimento per le visualizzazioni e i rapporti dei file di dati di profilatura generati tramite il metodo di concorrenza che includono dati di esecuzione di thread.|