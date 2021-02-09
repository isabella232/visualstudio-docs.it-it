---
title: Compatibilità del visualizzatore personalizzato Visual C/C++
description: Una nuova funzionalità di Visual Studio 2019 potrebbe non essere compatibile con i componenti aggiuntivi dell'analizzatore di espressioni C/C++ legacy e con i visualizzatori personalizzati. Vedi questo articolo per altri dettagli.
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
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32ad6b4b699f9cfe02739f341a4f9ddf29360f37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884312"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilità del visualizzatore personalizzato Visual C/C++

A partire da Visual Studio 2019, C++ include un debugger migliorato che usa un processo esterno a 64 bit per ospitare i componenti con utilizzo intensivo della memoria. Nell'ambito di questo aggiornamento, è necessario aggiornare alcune estensioni all'analizzatore di espressioni C/C++ per renderle compatibili con il nuovo debugger.

Se si sta attualmente utilizzando un componente aggiuntivo c/c++ EE legacy o un visualizzatore personalizzato c/c++, è possibile disattivare l'utilizzo di questo processo esterno passando a **strumenti**  >  **Opzioni**  >  **debug** e deselezionando i **simboli di debug di caricamento in processo esterno (solo nativo)**. Se si deseleziona questa opzione, si verificherà un aumento significativo dell'utilizzo della memoria all'interno del processo IDE (devenv.exe). Pertanto, se si prevede di eseguire il debug di progetti di grandi dimensioni, è consigliabile utilizzare il proprietario dell'estensione per renderlo compatibile con questa opzione di debug.

Se si è proprietari di un componente aggiuntivo C/C++ EE legacy o di un visualizzatore personalizzato C/C++, è possibile trovare altre informazioni sulla scelta di caricare l'estensione in un processo di lavoro nel [wiki degli esempi di estendibilità di Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). È anche possibile trovare un [esempio di visualizzatore personalizzato C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).