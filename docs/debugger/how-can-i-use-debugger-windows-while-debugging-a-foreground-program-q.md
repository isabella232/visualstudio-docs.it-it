---
title: Usare le finestre del debugger durante il debug di un'app in primo piano | Microsoft Docs
description: Se si esegue il debug di un programma che deve rimanere in primo piano, usare il debug remoto per evitare di metterlo in background.
ms.custom: SEO-VS-2020
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8009e7541fa848db1d1b0019eb24743bc0aca0c1e3d5bb22cb1b463aa260c3cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453895"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Come è possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano?
## <a name="problem-description"></a>Descrizione del problema
 Si sta tentando di effettuare il debug di un problema relativo a un disegno dello schermo. Per osservare questo problema è necessario mantenere il programma in primo piano, ma in questo modo è impossibile accedere alle finestre di debug. Come posso procedere?

## <a name="solution"></a>Soluzione
 Se si dispone di un secondo computer, sarà possibile ricorrere al debug remoto. Con una configurazione su due computer sarà possibile osservare il disegno dello schermo sul computer remoto mentre si esegue il debugger sull'host. Per altre informazioni sul debug remoto, vedere [Debug remoto](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)
