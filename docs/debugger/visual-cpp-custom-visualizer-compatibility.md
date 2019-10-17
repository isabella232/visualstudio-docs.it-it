---
title: Compatibilità del visualizzatoreC++ Visual C/Custom
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430625"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilità del visualizzatoreC++ Visual C/Custom

A partire da Visual Studio 2019 C++ , include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i componenti con utilizzo intensivo della memoria. Nell'ambito di questo aggiornamento, è necessario aggiornare alcune estensioni all'C++ analizzatore di espressioni C/Expression per renderle compatibili con il nuovo debugger.

Se attualmente si utilizza un componente aggiuntivo C/C++ EE legacy o un visualizzatore cC++ /personalizzato, è possibile disattivare l'utilizzo di questo processo esterno passando a **strumenti** > **Opzioni** > **debug**e quindi deselezionando il debug di **caricamento. simboli nel processo esterno (solo nativo)** . Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv. exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile utilizzare il proprietario dell'estensione per renderlo compatibile con questa opzione di debug.

Se si è il proprietario di un componente aggiuntivo CC++ /EE legacy o diC++ un visualizzatore c/personalizzato, è possibile trovare altre informazioni sulla scelta di caricare l'estensione in un processo di lavoro nel [wiki degli esempi di estendibilità di Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). È anche possibile trovare un [esempio diC++ visualizzatore C/personalizzato](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).