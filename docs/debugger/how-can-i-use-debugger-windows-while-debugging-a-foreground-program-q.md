---
title: Usare le finestre del debugger durante il debug di un'app in primo piano | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11bd61cda8c92721fb42c640b0b5100b8054acdf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698027"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Come è possibile utilizzare le finestre debugger mentre si esegue il debug di un programma in primo piano?
## <a name="problem-description"></a>Descrizione del problema
 Si sta tentando di effettuare il debug di un problema relativo a un disegno dello schermo. Per osservare questo problema è necessario mantenere il programma in primo piano, ma in questo modo è impossibile accedere alle finestre di debug. Come è possibile procedere?

## <a name="solution"></a>Soluzione
 Se si dispone di un secondo computer, sarà possibile ricorrere al debug remoto. Con una configurazione su due computer sarà possibile osservare il disegno dello schermo sul computer remoto mentre si esegue il debugger sull'host. Per altre informazioni sul debug remoto, vedere [debug remoto](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)