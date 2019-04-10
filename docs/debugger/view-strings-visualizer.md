---
title: Visualizzare le stringhe in un visualizzatore di stringhe | Microsoft Docs
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367309"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Stringhe di visualizzazione in un visualizzatore di stringhe in Visual Studio

Durante il debug in Visual Studio, è possibile visualizzare le stringhe con il Visualizzatore stringhe predefinite. Il Visualizzatore stringhe Mostra le stringhe che sono troppo lunghi per una finestra del debugger o suggerimento dati. Può anche consentono di identificare le stringhe in formato non valido.

Il Visualizzatore stringhe predefinito include i testo normale, XML, HTML e JSON opzioni. È anche possibile aprire i visualizzatori predefiniti per alcuni altri tipi, ad esempio [DataSet, DataTable e DataView](../debugger/dataset-visualizer-dialog-box.md) oggetti, dalle **Auto** o altre finestre del debugger.

> [!NOTE]
> Se è necessario esaminare gli elementi XAML o UI WPF in un visualizzatore, vedere o [delle proprietà di ispezionare XAML durante il debug](../debugger/inspect-xaml-properties-while-debugging.md) oppure [come usare il Visualizzatore dell'albero WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Aprire un visualizzatore di stringhe

Per aprire il Visualizzatore stringhe, è necessario essere messo in pausa durante il debug. Passare il mouse su una variabile con un testo normale, XML, HTML o JSON valore stringa e selezionare l'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore").

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "Visualizzatore stringhe Open")

## <a name="view-string-visualizer-data"></a>Visualizzare i dati del Visualizzatore di stringhe

Nella finestra del Visualizzatore di stringa, il **espressione** campo Mostra la variabile o espressione passa il mouse, e il **valore** campo viene visualizzato il valore della stringa.

Uno spazio vuoto **valore** significa che il Visualizzatore scelto non riconosce la stringa. Ad esempio, il **visualizzatore XML** Mostra un valore vuoto **valore** per una stringa di testo senza tag XML o una stringa JSON.

Per visualizzare le stringhe che il Visualizzatore scelto non è in grado di riconoscere, scegliere il **Visualizzatore testo**. Il **Visualizzatore testo** Mostra testo normale.

### <a name="view-json-string-data"></a>Visualizzare i dati di stringa JSON

Una stringa JSON ben formata risulterà simile alla figura seguente nel Visualizzatore di JSON. JSON non può visualizzare un'icona di errore (o vuoto se non riconosciuto). Per identificare l'errore JSON, copiare e incollare la stringa in uno strumento di Lint JSON, ad esempio [JSLint](https://www.jslint.com/).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore stringhe JSON")

### <a name="view-xml-string-data"></a>Visualizzare i dati di stringa XML

Una stringa XML ben formata risulterà simile alla figura seguente nel visualizzatore XML. XML non valido potrebbe visualizzare senza il tag XML oppure lasciare vuoto se non è stata riconosciuta.

![Visualizzatore di stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore stringhe XML")

### <a name="view-html-string-data"></a>Dati di stringa di visualizzazione HTML

Verrà visualizzata una stringa HTML ben formata come se viene eseguito il rendering in un browser, come illustrato nella figura seguente. HTML non corretto potrebbero visualizzati come testo normale.

![Visualizzatore stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore stringhe HTML")

## <a name="see-also"></a>Vedere anche

- [Creazione di visualizzatori personalizzati (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations)