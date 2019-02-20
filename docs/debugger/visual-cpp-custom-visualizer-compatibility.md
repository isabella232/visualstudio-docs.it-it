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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335181"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilità di Visual C/C++ visualizzatore personalizzato

A partire da Visual Studio 2019, Visual C++ include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i relativi componenti a elevato utilizzo di memoria. Come parte di questo aggiornamento, è necessario aggiornare alcune estensioni per l'analizzatore di espressioni di Visual C/C++ per renderli compatibili con il nuovo debugger.

Se si sta utilizzando attualmente un componente aggiuntivo di C/C++ EE legacy o un visualizzatore personalizzato di C/C++, è possibile disattivare l'utilizzo di questo processo esterno visitando **degli strumenti** > **opzioni**  >   **Debugging**e quindi deselezionando **i simboli di debug di carico in processo esterno (solo nativo)**. Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv.exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile rivolgersi al proprietario dell'estensione di assicurare la compatibilità con questa opzione di debug.

Se sei il proprietario di un componente aggiuntivo di C/C++ EE legacy o di un visualizzatore personalizzato di C/C++, è possibile trovare altre informazioni sul consenso esplicito al caricamento dell'estensione in un processo di lavoro nella [wiki di esempi di estendibilità Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). È anche possibile trovare un [esempio di visualizzatore personalizzato di C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).