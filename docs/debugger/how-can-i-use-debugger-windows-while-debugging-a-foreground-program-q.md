---
title: Usare le finestre del debugger durante il debug di un'app in primo piano | Microsoft Docs
description: Se si esegue il debug di un programma che deve rimanere in primo piano, utilizzare il debug remoto per evitare di inserirlo in background.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03a143ee2d04227171895bf2b14dff92545b9952
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155094"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Come è possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano?
## <a name="problem-description"></a>Descrizione del problema
 Si sta tentando di effettuare il debug di un problema relativo a un disegno dello schermo. Per osservare questo problema è necessario mantenere il programma in primo piano, ma in questo modo è impossibile accedere alle finestre di debug. Come posso procedere?

## <a name="solution"></a>Soluzione
 Se si dispone di un secondo computer, sarà possibile ricorrere al debug remoto. Con una configurazione su due computer sarà possibile osservare il disegno dello schermo sul computer remoto mentre si esegue il debugger sull'host. Per ulteriori informazioni sul debug remoto, vedere [Remote Debugging](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
