---
title: Visualizzare le stringhe in un visualizzatore di stringhe | Microsoft Docs
description: Usare il visualizzatore di stringhe nel debugger Visual Studio per visualizzare stringhe di testo, XML, HTML e JSON. È possibile visualizzare altri tipi di oggetto, tra cui DataSet e DataTable.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 53201659ee729e142b215a38971a7d9cbd62afebc9d9aa3c72ef315ce58a2658
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418759"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Visualizzare le stringhe in un visualizzatore di stringhe in Visual Studio

Durante il debug in Visual Studio, è possibile visualizzare le stringhe con il visualizzatore di stringhe incorporato. Il visualizzatore di stringhe mostra le stringhe troppo lunghe per un suggerimento dati o una finestra del debugger. Consente anche di identificare stringhe in formato non valido.

Il visualizzatore di stringhe incorporato include opzioni testo normale, XML, HTML e JSON. È anche possibile aprire visualizzatori predefiniti per alcuni altri tipi, ad esempio oggetti [DataSet, DataTable e DataView,](../debugger/dataset-visualizer-dialog-box.md) dalle finestre Auto o altre finestre del debugger. 

> [!NOTE]
> Se è necessario esaminare gli elementi DELL'interfaccia utente XAML o WPF in un visualizzatore, vedere o Controllare le proprietà [XAML](../xaml-tools/inspect-xaml-properties-while-debugging.md) durante il debug o Come usare [il visualizzatore ad](../debugger/how-to-use-the-wpf-tree-visualizer.md)albero WPF.

## <a name="open-a-string-visualizer"></a>Aprire un visualizzatore di stringhe

Per aprire il visualizzatore di stringhe, è necessario essere sospesi durante il debug. Passare il mouse su una variabile con un valore stringa testo normale, XML, HTML o JSON e selezionare l'icona della lente di ingrandimento ![VisualizzatoreIcona](../debugger/media/dbg-tips-visualizer-icon.png "Icona visualizzatore").

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "Aprire il visualizzatore di stringhe")

## <a name="view-string-visualizer-data"></a>Visualizzare i dati del visualizzatore di stringhe

Nella finestra del visualizzatore  di stringhe il campo Espressione mostra la variabile o l'espressione su cui si passa il mouse e il campo **Valore** mostra il valore della stringa.

Un valore **vuoto** indica che il visualizzatore scelto non è in grado di riconoscere la stringa. Ad esempio, il **visualizzatore XML** mostra un valore **vuoto** per una stringa di testo senza tag XML o una stringa JSON.

Per visualizzare le stringhe che il visualizzatore scelto non è in grado di riconoscere, scegliere **visualizzatore di testo.** Il **visualizzatore di testo** mostra testo normale.

### <a name="view-json-string-data"></a>Visualizzare i dati stringa JSON

Una stringa JSON ben formata è simile alla figura seguente nel visualizzatore JSON. Json in formato non valido può visualizzare un'icona di errore (o vuoto se non riconosciuto). Per identificare l'errore JSON, copiare e incollare la stringa in uno strumento di lint JSON, ad esempio [JSLint.](https://www.jslint.com/)

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore di stringhe JSON")

### <a name="view-xml-string-data"></a>Visualizzare i dati di tipo stringa XML

Una stringa XML ben formata è simile alla figura seguente nel visualizzatore XML. Il formato XML non valido può essere visualizzato senza i tag XML o vuoto se non riconosciuto.

![Visualizzatore di stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore di stringhe XML")

### <a name="view-html-string-data"></a>Visualizzare i dati di stringa HTML

Una stringa HTML ben formata viene visualizzata come se ne fosse eseguito il rendering in un browser, come illustrato nella figura seguente. Html in formato non valido può essere visualizzato come testo normale.

![Visualizzatore di stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore di stringhe HTML")

## <a name="see-also"></a>Vedi anche

- [Creare visualizzatori personalizzati (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations)