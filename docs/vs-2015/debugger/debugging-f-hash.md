---
title: 'Debug di F # | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd722e40a0579181e3c361706f0775aaf350c341
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209573"
---
# <a name="debugging-f"></a>Debug di F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug di F #è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:  
  
-   Il **Auto** non vengono visualizzate le variabili F #.  
  
-   La modifica e la continuazione non sono supportate per F#. La modifica del codice F# durante una sessione di debug è possibile ma deve essere evitata. Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.  
  
-   Il debugger non riconosce le espressioni F#. Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F#, è necessario tradurre l'espressione nella sintassi C#. Quando si traduce un'espressione F# in C#, ricordare che C# utilizza == come operatore di confronto per uguaglianza e che F# utilizza un solo =.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)



