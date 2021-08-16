---
title: Utilizzo della legenda della visualizzazione Grafici per analizzare i test di carico
description: Informazioni sulla visualizzazione Grafici dell'Analizzatore test di carico, che include un pannello della legenda che visualizza informazioni sui contatori delle prestazioni per un grafico selezionato.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9875a8a95f0fb32a26e70cacb8a43eede05321631698906c5d6dd07e9645a585
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384698"
---
# <a name="use-the-graphs-view-legend-to-analyze-load-tests"></a>Usare la legenda della visualizzazione Grafici per analizzare i test di carico

Nella visualizzazione Grafici dell'analizzatore test di carico è incluso un riquadro legenda in cui vengono visualizzate le informazioni per ogni contatore delle prestazioni associato al grafico attualmente selezionato.

![Legenda della visualizzazione grafici](../test/media/load_viewlegend.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nella legenda sono contenute le informazioni seguenti:

- **Visualizzazione nel grafico:** usare le caselle di controllo per specificare se la linea relativa a un particolare contatore, ad esempio **Carico utente** o **Errori/sec**, viene tracciata sul grafico. Selezionare una casella di controllo se si desidera che la relativa riga venga tracciata nel grafico. Per rimuovere una linea del tracciato dal grafico, deselezionare la relativa casella di controllo. Quando viene rimossa una linea del tracciato, le statistiche per il contatore continuano ad essere visualizzate nella legenda.

- **Intervallo:** in questa colonna viene visualizzato l'intervallo dell'asse y del contatore delle prestazioni. Per impostazione predefinita, questo valore verrà regolato automaticamente secondo le modifiche all'intervallo dei dati di esempio. Un intervallo regolato automaticamente sarà sempre maggiore di una potenza di 10 rispetto al valore Max. Ciò include potenze di 10 negative. Un grafico può contenere una varietà di contatori, ciascuno con un intervallo diverso. Pertanto, l'asse y non è identificato da nessun intervallo specifico, ma è identificato da valori da 0 a 100 che rappresentano una percentuale dell'intervallo totale per ciascun contatore. Per un contatore con un intervallo di 1000, ad esempio, un punto dati di 60 sull'asse y corrisponderebbe a un valore di 600 per il contatore.

    > [!NOTE]
    > È possibile disabilitare la regolazione automatica del valore di intervallo bloccando l'intervallo su un valore specifico. Quando viene bloccato l'intervallo, qualsiasi valore che lo superi verrà visualizzato come valore massimo specificato all'inizio del grafico. Usare la finestra di dialogo **Opzioni tracciato** per bloccare l'intervallo su un valore specifico.

- **Contatore:** le quattro colonne denominate **Contatore**, **Istanza**, **Categoria** e **Computer** identificano insieme in modo univoco il contatore delle prestazioni.

- **Colore:** nella colonna **Colore** vengono visualizzati il colore e lo stile della linea del tracciato per il contatore delle prestazioni. La finestra di dialogo **Opzioni tracciato** consente di modificare il colore o lo stile della linea di un contatore delle prestazioni nel grafico. La finestra di dialogo **Opzioni tracciato** è disponibile dal menu di scelta rapida della legenda.

- **Statistiche:** nelle colonne **Min**, **Max**, **Media** e **Ultimo** vengono visualizzate le rispettive statistiche per il contatore delle prestazioni. I valori corrispondono ai dati visualizzati nell'area visibile del grafico. Se ad esempio, si ingrandisce l'area di un'esecuzione, le statistiche della legenda riporteranno valori solo per l'area ingrandita. La colonna "Ultimo" corrisponde al valore del contatore delle prestazioni dell'intervallo di campionamento completato più recentemente.

    > [!NOTE]
    > La colonna Ultimo viene visualizzata solo nella legenda dell'analizzatore test di carico mentre il test è in esecuzione.

     Per altre informazioni, vedere [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

La selezione di un elemento nella legenda consente di effettuare le operazioni seguenti:

- Consente la rimozione dell'elemento dalla legenda e dal grafico. Fare clic con il pulsante destro del mouse su un elemento e scegliere **Elimina** oppure premere **CANC**.

- Consente di evidenziare la linea del tracciato nel grafico.

- Consente di visualizzare i dati per l'elemento selezionato nella griglia dei dati.

- Consente di accedere alla finestra di dialogo **Opzioni tracciato** per il contatore.

> [!TIP]
> È possibile usare il pulsante del menu a discesa **Opzioni grafico** sulla barra degli strumenti dell'**Analizzatore test di carico** e selezionare **Mostra legenda** per visualizzare o nascondere il riquadro **Legenda** associato alla visualizzazione del grafico.

## <a name="see-also"></a>Vedi anche

- [Procedura: Eseguire lo zoom avanti su un'area del grafico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizzare i risultati dei test di carico nella visualizzazione Grafici](../test/analyze-load-test-results-in-the-graphs-view.md)
