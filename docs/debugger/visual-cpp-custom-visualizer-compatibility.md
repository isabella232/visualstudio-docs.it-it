---
title: Compatibilità di Visual C/C++ visualizzatore personalizzato
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: a51f2d87b432bf6f4a3925b55622273b56cf5c32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920964"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilità di Visual C/C++ visualizzatore personalizzato

A partire da Visual Studio 2019, Visual C++ include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i relativi componenti a elevato utilizzo di memoria. Come parte di questo aggiornamento, è necessario aggiornare alcune estensioni per l'analizzatore di espressioni di Visual C/C++ per renderli compatibili con il nuovo debugger.

Se si sta utilizzando attualmente un componente aggiuntivo di C/C++ EE legacy o un visualizzatore personalizzato di C/C++, è possibile disattivare l'utilizzo di questo processo esterno visitando **degli strumenti** > **opzioni**  >   **Debugging**e quindi deselezionando **i simboli di debug di carico in processo esterno (solo nativo)**. Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv.exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile rivolgersi al proprietario dell'estensione di assicurare la compatibilità con questa opzione di debug.

Se sei il proprietario di un componente aggiuntivo di C/C++ EE legacy o di un visualizzatore personalizzato di C/C++, è possibile trovare altre informazioni sul consenso esplicito al caricamento dell'estensione in un processo di lavoro nella [wiki di esempi di estendibilità Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). È anche possibile trovare un [esempio di visualizzatore personalizzato di C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).