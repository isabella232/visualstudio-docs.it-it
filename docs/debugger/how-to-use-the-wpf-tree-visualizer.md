---
title: Usare il visualizzatore albero WPF | Microsoft Docs
description: Usare il Windows Presentation Foundation (WPF) per esplorare la struttura ad albero visuale di un oggetto WPF e per visualizzare le proprietà di dipendenza WPF in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 76a32b8fb6f6c61c27f673b150ec75541ce244f0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709910"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Procedura: utilizzare il visualizzatore della struttura ad albero di WPF
È possibile utilizzare il visualizzatore dell'albero di WPF per esplorare la struttura ad albero visuale di un oggetto WPF e visualizzare le proprietà di dipendenza WPF per gli oggetti contenuti in tale albero. Per altre informazioni sugli alberi visivi, vedere [Alberi in WPF.](/dotnet/framework/wpf/advanced/trees-in-wpf) Per altre informazioni sulle proprietà di dipendenza, vedere [Cenni preliminari sulle proprietà di dipendenza](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Quando si apre il visualizzatore albero WPF, vengono  visualizzati due riquadri: Albero visuale a sinistra e Proprietà del nome  **:**_Tipo_ a destra. Selezionare qualsiasi oggetto nel riquadro **Albero visuale** e il riquadro Proprietà **di** _Nome_**:** Tipo viene aggiornato automaticamente per visualizzare le proprietà dell'oggetto.

 > [!NOTE]
 > È anche possibile usare la struttura [ad albero visuale live](../xaml-tools/inspect-xaml-properties-while-debugging.md) e Esplora proprietà live per esaminare la struttura ad albero visuale degli oggetti WPF. Il visualizzatore albero WPF è una funzionalità legacy e non è in fase di sviluppo attivo.

### <a name="to-open-the-wpf-tree-visualizer"></a>Per aprire il visualizzatore della struttura ad albero di WPF

1. In un suggerimento dati, in una finestra **Espressioni di controllo**, **Auto** o **Variabili locali** fare clic sulla freccia della lente d'ingrandimento accanto al nome di un oggetto WPF.

     Verrà visualizzato un elenco di visualizzatori.

2. Fare clic su **Visualizzatore dell'albero di WPF**.

### <a name="to-search-the-visual-tree"></a>Per eseguire ricerche nella struttura ad albero visuale

- Nel riquadro **Struttura ad albero visuale**, digitare la stringa da cercare nella casella **Cerca**.

  Il visualizzatore della struttura ad albero di WPF troverà immediatamente il primo oggetto nella struttura ad albero visuale che corrisponde alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.

  - Per passare alla corrispondenza successiva all'interno della struttura ad albero visuale, fare clic su **Successiva**.

  - Per ritornare alla corrispondenza precedente, fare clic su **Prec**.

  - Per cancellare i criteri di ricerca, fare clic su **Cancella**.

### <a name="to-search-the-properties-list"></a>Per eseguire ricerche nell'elenco di proprietà

- Nel riquadro **Proprietà di** _Nome_**:**_Tipo_ digitare la stringa da cercare nella **casella** Filtro.

  Il visualizzatore della struttura ad albero di WPF troverà immediatamente le proprietà che corrispondono alla stringa digitata; nell'elenco sono visualizzate soltanto le proprietà corrispondenti alla stringa digitata. Digitare più caratteri per trovare una corrispondenza più accurata.

  - Per cancellare i criteri di ricerca, fare clic su **Cancella**.

### <a name="to-close-the-visualizer"></a>Per chiudere il visualizzatore

- Fare clic sull'icona **Chiudi** nell'angolo in alto a destra della finestra di dialogo.

## <a name="see-also"></a>Vedi anche
- [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Strutture ad albero in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Panoramica delle proprietà di dipendenza](/dotnet/framework/wpf/advanced/dependency-properties-overview)
