---
title: 'Debug di F # | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7bc3934136f0966439bec2e4368488e52099602
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738261"
---
# <a name="debugging-f"></a>Debug di F\#
Il debug di F #è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:

- Nella finestra **Auto** non vengono visualizzate le variabili F#.

- La modifica e la continuazione non sono supportate per F#. La modifica del codice F# durante una sessione di debug è possibile ma deve essere evitata. Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.

- Il debugger non riconosce le espressioni F#. Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F#, è necessario tradurre l'espressione nella sintassi C#. Quando si traduce un'espressione F# in C#, ricordare che C# utilizza == come operatore di confronto per uguaglianza e che F# utilizza un solo =.

## <a name="see-also"></a>Vedere anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
