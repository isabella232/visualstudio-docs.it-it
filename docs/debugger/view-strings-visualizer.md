---
title: Visualizzare le stringhe in un visualizzatore di stringhe | Microsoft Docs
description: Usare il Visualizzatore di stringhe nel debugger di Visual Studio per visualizzare stringhe di testo, XML, HTML e JSON. È possibile visualizzare altri tipi di oggetti, inclusi DataSet e DataTable.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d13e5f5c3ee5a82a56dd8c98fa37e3e13e5169d5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149937"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visualizzare le stringhe in un visualizzatore di stringhe in Visual Studio

Durante il debug in Visual Studio, è possibile visualizzare le stringhe con il Visualizzatore di stringhe incorporato. Il Visualizzatore di stringhe Mostra stringhe troppo lunghe per un suggerimento dati o una finestra del debugger. Consente inoltre di identificare stringhe in formato non valido.

Il Visualizzatore di stringhe incorporato include le opzioni testo normale, XML, HTML e JSON. È anche possibile aprire i visualizzatori predefiniti per alcuni altri tipi, ad esempio [DataSet, DataTable e oggetti DataView](../debugger/dataset-visualizer-dialog-box.md) , dalle finestre **auto** o altre finestre del debugger.

> [!NOTE]
> Se è necessario controllare gli elementi dell'interfaccia utente XAML o WPF in un visualizzatore, vedere o [controllare le proprietà XAML durante il debug](../xaml-tools/inspect-xaml-properties-while-debugging.md) o [come usare il Visualizzatore dell'albero di WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Apre un visualizzatore di stringhe

Per aprire il Visualizzatore di stringhe, è necessario sospendere l'oggetto durante il debug. Passare il puntatore del mouse su una variabile con un valore di stringa testo normale, XML, HTML o JSON e selezionare l'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore").

![Apre un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "Apri Visualizzatore stringhe")

## <a name="view-string-visualizer-data"></a>Visualizza dati Visualizzatore stringhe

Nella finestra Visualizzatore stringhe il campo **espressione** Mostra la variabile o l'espressione su cui si sta passando il mouse e il campo **valore** indica il valore stringa.

Un **valore** vuoto indica che il Visualizzatore scelto non è in grado di riconoscere la stringa. Ad esempio, il **Visualizzatore XML** Mostra un **valore** vuoto per una stringa di testo senza tag XML o una stringa JSON.

Per visualizzare le stringhe non riconosciute dal Visualizzatore scelto, scegliere il **Visualizzatore di testo**. Il **Visualizzatore di testo** Mostra il testo normale.

### <a name="view-json-string-data"></a>Visualizza dati stringa JSON

Una stringa JSON ben formata appare simile alla figura seguente nel Visualizzatore JSON. JSON in formato non valido potrebbe visualizzare un'icona di errore (oppure vuota se non riconosciuta). Per identificare l'errore JSON, copiare e incollare la stringa in uno strumento JSON, ad esempio [JSLint](https://www.jslint.com/).

![Visualizzatore stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore stringhe JSON")

### <a name="view-xml-string-data"></a>Visualizza dati stringa XML

Una stringa XML ben formata è simile alla figura seguente nel Visualizzatore XML. Il formato XML non valido può essere visualizzato senza i tag XML oppure vuoto se non riconosciuto.

![Visualizzatore stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore stringhe XML")

### <a name="view-html-string-data"></a>Visualizza dati stringa HTML

Una stringa HTML ben formata viene visualizzata come se ne venisse eseguito il rendering in un browser, come illustrato nella figura seguente. Il formato HTML non valido potrebbe essere visualizzato come testo normale.

![Visualizzatore stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore stringhe HTML")

## <a name="see-also"></a>Vedere anche

- [Creare visualizzatori personalizzati (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations)