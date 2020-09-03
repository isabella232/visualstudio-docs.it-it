---
title: Finestra di dialogo Visualizzatore stringhe | Microsoft Docs
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430825"
---
# <a name="string-visualizer-dialog-box"></a>Finestra di dialogo Visualizzatore stringhe

Durante il debug in Visual Studio, è possibile visualizzare le stringhe con il Visualizzatore di stringhe incorporato. Il Visualizzatore di stringhe Mostra stringhe troppo lunghe per un suggerimento dati o una finestra del debugger. Consente inoltre di identificare stringhe in formato non valido.

Il Visualizzatore di stringhe incorporato include le opzioni testo normale, XML, HTML e JSON. È anche possibile aprire i visualizzatori predefiniti per alcuni altri tipi, ad esempio [DataSet, DataTable e oggetti DataView](../debugger/dataset-visualizer-dialog-box.md) , dalle finestre **auto** o altre finestre del debugger.

> [!NOTE]
> Se è necessario controllare gli elementi dell'interfaccia utente XAML o WPF in un visualizzatore, vedere o [controllare le proprietà XAML durante il debug](../xaml-tools/inspect-xaml-properties-while-debugging.md) o [come usare il Visualizzatore dell'albero di WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md).

Per aprire il Visualizzatore di stringhe, è necessario sospendere l'oggetto durante il debug. Passare il puntatore del mouse su una variabile con un valore di stringa testo normale, XML, HTML o JSON e selezionare l'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del Visualizzatore").

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

Il campo **espressione** Mostra la variabile o l'espressione su cui si sta passando il puntatore del mouse.

Campo **valore** indica il valore stringa. Un **valore** vuoto indica che il Visualizzatore scelto non è in grado di riconoscere la stringa. Ad esempio, il **Visualizzatore XML** Mostra un **valore** vuoto per una stringa di testo senza tag XML o una stringa JSON. Per visualizzare le stringhe non riconosciute dal Visualizzatore scelto, scegliere invece il **Visualizzatore di testo** . Il **Visualizzatore di testo** Mostra il testo normale.

### <a name="json-string-data"></a>Dati stringa JSON

Una stringa JSON ben formata appare simile alla figura seguente nel Visualizzatore JSON. JSON in formato non valido potrebbe visualizzare un'icona di errore (oppure vuota se non riconosciuta). Per identificare l'errore JSON, copiare e incollare la stringa in uno strumento JSON, ad esempio [JSLint](https://www.jslint.com/).

![Visualizzatore stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore stringhe JSON")

### <a name="xml-string-data"></a>Dati stringa XML

Una stringa XML ben formata è simile alla figura seguente nel Visualizzatore XML. Il formato XML non valido può essere visualizzato senza i tag XML oppure vuoto se non riconosciuto.

![Visualizzatore stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore stringhe XML")

### <a name="html-string-data"></a>Dati stringa HTML

Una stringa HTML ben formata viene visualizzata come se ne venisse eseguito il rendering in un browser, come illustrato nella figura seguente. Il formato HTML non valido potrebbe essere visualizzato come testo normale.

![Visualizzatore stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore stringhe HTML")

## <a name="see-also"></a>Vedere anche

- [Creare visualizzatori personalizzati (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations)