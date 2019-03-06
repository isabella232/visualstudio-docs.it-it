---
title: Debug di F# | Microsoft Docs
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
ms.openlocfilehash: 11a310884f9f63264157c96bafc15e8161c0239d
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323841"
---
# <a name="debugging-f"></a>Debug di F\#
Il debug di F #è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:

-   Nella finestra **Auto** non vengono visualizzate le variabili F#.

-   La modifica e la continuazione non sono supportate per F#. La modifica del codice F# durante una sessione di debug è possibile ma deve essere evitata. Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.

-   Il debugger non riconosce le espressioni F#. Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F#, è necessario tradurre l'espressione nella sintassi C#. Quando si traduce un'espressione F# in C#, ricordare che C# utilizza == come operatore di confronto per uguaglianza e che F# utilizza un solo =.

## <a name="see-also"></a>Vedere anche
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
