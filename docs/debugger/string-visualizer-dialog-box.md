---
title: Finestra di dialogo Visualizzatore di stringhe | Microsoft Docs
description: Visualizzare le stringhe con la finestra di dialogo Del visualizzatore di stringhe predefinita durante il debug in Visual Studio.
ms.date: 10/10/2018
ms.custom: contperf-fy21q4
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 52d50d7e2bf204de7907f568318b100aa53349d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146680"
---
# <a name="string-visualizer-dialog-box"></a>Finestra di dialogo Visualizzatore stringhe

Durante il debug in Visual Studio, è possibile visualizzare le stringhe con il visualizzatore di stringhe incorporato. Il visualizzatore di stringhe mostra stringhe troppo lunghe per una descrizione comando dati o una finestra del debugger. Può anche essere utile per identificare stringhe in formato non valido.

I visualizzatori di stringhe predefiniti includono [le opzioni Text](#text-string-data), [XML](#xml-string-data), [HTML](#html-string-data) [e JSON.](#json-string-data) È anche possibile aprire visualizzatori predefiniti per alcuni altri tipi, ad esempio [oggetti DataSet, DataTable e DataView,](../debugger/dataset-visualizer-dialog-box.md) dalle finestre Auto **o** altre finestre del debugger.

> [!NOTE]
> Se è necessario esaminare gli elementi DELL'interfaccia utente XAML o WPF in un visualizzatore, vedere o Esaminare le proprietà [XAML](../xaml-tools/inspect-xaml-properties-while-debugging.md) durante il debug o Come usare il visualizzatore albero [WPF.](../debugger/how-to-use-the-wpf-tree-visualizer.md)

Per aprire il visualizzatore di stringhe, è necessario essere sospesi durante il debug. Passare il puntatore del mouse su una variabile con un testo normale, un valore di stringa XML, HTML o JSON e selezionare l'icona della lente di ingrandimento ![VisualizzatoreIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icona del visualizzatore").

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Il** campo Espressione mostra la variabile o l'espressione su cui si passa il mouse.

**Il campo** Valore mostra il valore stringa. Un valore **vuoto** indica che il visualizzatore scelto non è in grado di riconoscere la stringa. Ad esempio, il **visualizzatore XML** mostra un **valore vuoto** per una stringa di testo senza tag XML o una stringa JSON. Per visualizzare le stringhe che il visualizzatore scelto non è in grado di riconoscere, scegliere il **visualizzatore di** testo. Il **visualizzatore di testo** mostra testo normale.

### <a name="text-string-data"></a>Dati stringa di testo

Il **visualizzatore di testo** mostra testo normale. Se è necessaria una formattazione personalizzata per una stringa C++, creare una [visualizzazione Natvis](../debugger/create-custom-views-of-native-objects.md).

![Visualizzatore di stringhe di testo](../debugger/media/dbg-string-visualizer-text.png "Visualizzatore di stringhe di testo")

### <a name="json-string-data"></a>Dati stringa JSON

Una stringa JSON ben formata è simile alla figura seguente nel visualizzatore JSON. Json in formato non valido può visualizzare un'icona di errore (o vuota se non riconosciuta). Per identificare l'errore JSON, copiare e incollare la stringa in uno strumento di linting JSON, ad esempio [JSLint](https://www.jslint.com/).

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore di stringhe JSON")

### <a name="xml-string-data"></a>Dati di stringa XML

Una stringa XML ben formata è simile alla figura seguente nel visualizzatore XML. Xml in formato non valido può essere visualizzato senza tag XML o vuoto se non riconosciuto.

![Visualizzatore di stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore di stringhe XML")

### <a name="html-string-data"></a>Dati di stringa HTML

Una stringa HTML ben formata viene visualizzata come se ne fosse eseguito il rendering in un browser, come illustrato nella figura seguente. Html in formato non valido può essere visualizzato come testo normale.

![Visualizzatore di stringhe HTML](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore di stringhe HTML")

## <a name="see-also"></a>Vedi anche

- [Creare visualizzatori personalizzati (C#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations)