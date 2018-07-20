---
title: Visualizzare le stringhe in un visualizzatore di stringhe | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151034"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Stringhe di visualizzazione in un visualizzatore di stringhe in Visual Studio
Durante il debug, è possibile aprire un visualizzatore di stringhe per le stringhe di visualizzazione che sono troppo lunghi per visualizzare in una finestra del debugger o suggerimento dati. In molti scenari, il visualizzatore può aiutare a identificare le stringhe in formato non valido.

I visualizzatori stringa predefinite standard includono testo normale, XML, HTML e JSON. Per alcuni altri tipi, ad esempio gli oggetti WPF che vengono visualizzati nel debugger di windows, ad esempio la **Auto** finestra, è anche possibile aprire i visualizzatori.

## <a name="open-a-string-visualizer"></a>Aprire un visualizzatore di stringhe

Per visualizzare un testo normale, una stringa XML, HTML o JSON, fare clic sull'icona della lente di ingrandimento ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icona Visualizzatore") al passaggio del mouse su una variabile che contiene un valore stringa. Deve essere sospesa nel debugger per visualizzare l'icona della lente di ingrandimento.

![Aprire un visualizzatore di stringhe](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Visualizzare i dati stringa

Il **espressione** campo nel Visualizzatore di stringa viene visualizzata la variabile corrente o l'espressione è posizionato nel debugger.

Il **valore** campo viene visualizzato il valore della stringa. Il Visualizzatore di testo Mostra il testo normale.

Uno spazio vuoto **valore** indica che il visualizzatore specifico sia in grado di riconoscere il tipo di stringa. Ad esempio, il visualizzatore XML mostra un valore vuoto **valore** per una stringa di testo (con nessun tag XML) o un oggetto JSON formattato stringa. Se si desidera visualizzare una stringa non riconoscibile in un visualizzatore, usare il Visualizzatore di testo.

### <a name="view-json-string-data"></a>Visualizzare i dati di stringa JSON

Una stringa JSON ben formata risulterà simile al seguente nel Visualizzatore di JSON. JSON non può visualizzare un'icona di errore (o vuoto se non riconosciuto). Se viene visualizzata un'icona di errore, copiare e incollare la stringa JSON in uno strumento di Lint JSON, ad esempio [JSLint](https://www.jslint.com/) per identificare l'errore JSON.

![Visualizzatore di stringhe JSON](../debugger/media/dbg-tips-string-visualizer-json.png "Visualizzatore stringhe JSON")

### <a name="view-xml-string-data"></a>Visualizzare i dati di stringa XML

Una stringa in formato XML sarà simile a quanto illustrato di seguito nel visualizzatore XML. XML non valido potrebbe essere visualizzata senza i tag XML (o vuoto se non riconosciuto).

![Visualizzatore di stringhe XML](../debugger/media/dbg-string-visualizers-xml.png "Visualizzatore stringhe XML")

### <a name="view-html-string-data"></a>Dati di stringa di visualizzazione HTML

Una stringa HTML ben formata risulterà simile alla visualizzazione che si vedrebbe se la stringa viene eseguito il rendering in un browser, come illustrato nella figura seguente. HTML non corretto potrebbero visualizzati come testo normale.

![Stringa HTML Visualizer](../debugger/media/dbg-string-visualizers-html.png "Visualizzatore stringhe HTML")

## <a name="see-also"></a>Vedere anche  
 [Creazione di visualizzatori personalizzati (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)