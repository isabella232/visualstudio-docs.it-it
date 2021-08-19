---
title: Compatibilità del visualizzatore personalizzato di Visual C/C++
description: Una nuova funzionalità di Visual Studio 2019 potrebbe non essere compatibile con i componenti aggiuntivi legacy dell'analizzatore di espressioni C/C++ e i visualizzatori personalizzati. Vedi questo articolo per altri dettagli.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4948a4a3b82e4b713d590ffc9c8f8283ca495ea4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051807"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilità del visualizzatore personalizzato di Visual C/C++

A partire Visual Studio 2019, C++ include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i componenti a elevato utilizzo di memoria. Come parte di questo aggiornamento, alcune estensioni dell'analizzatore di espressioni C/C++ devono essere aggiornate per renderle compatibili con il nuovo debugger.

Se attualmente si usa un componente aggiuntivo edizione Enterprise C/C++ legacy o un visualizzatore personalizzato C/C++, è possibile disattivare l'utilizzo di questo processo esterno selezionando Strumenti Opzioni debug e deselezionando Carica simboli di debug nel processo esterno  >    >   **(solo nativo).** Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv.exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile collaborare con il proprietario dell'estensione per renderla compatibile con questa opzione di debug.

Se si è proprietari di un componente aggiuntivo edizione Enterprise C/C++ legacy o di un visualizzatore personalizzato C/C++, è possibile trovare altre informazioni su come acconsentire esplicitamente al caricamento dell'estensione in un processo di lavoro nel wiki degli esempi di estendibilità [di Concord.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting) È anche possibile trovare un esempio [di visualizzatore personalizzato C/C++.](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)