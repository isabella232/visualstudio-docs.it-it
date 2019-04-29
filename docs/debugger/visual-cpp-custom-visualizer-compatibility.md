---
title: Visual C# /C++ compatibilità di visualizzatore personalizzato
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901166"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C# /C++ compatibilità di visualizzatore personalizzato

A partire da Visual Studio 2019, oggetto visivo C++ include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i relativi componenti a elevato utilizzo di memoria. Come parte di questo aggiornamento, determinate estensioni per Visual C /C++ analizzatore di espressioni deve essere aggiornato per renderli compatibili con il nuovo debugger.

Se attualmente si sta utilizzando C legacy /C++ EE addin o C /C++ visualizzatore personalizzato, è possibile disattivare l'utilizzo di questo processo esterno visitando **Tools** > **opzioni**  >  **Debugging**e quindi deselezionando **simboli di debug di carico in processo esterno (solo nativo)**. Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv.exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile rivolgersi al proprietario dell'estensione di assicurare la compatibilità con questa opzione di debug.

Se sei il proprietario di un C legacy /C++ EE addin o C /C++ visualizzatore personalizzato, è possibile trovare altre informazioni sul consenso esplicito al caricamento dell'estensione in un processo di lavoro nella [wiki di esempi di estendibilità Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). È anche possibile trovare un [C /C++ esempio di visualizzatore personalizzato](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).