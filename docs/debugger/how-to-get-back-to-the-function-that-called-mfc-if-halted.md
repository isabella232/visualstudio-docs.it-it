---
title: Tornare alla funzione che ha chiamato MFC se interrotta | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef96bab28b1a17d4f20728a393511720fd10c624
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349471"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedura: tornare alla funzione che ha chiamato MFC se interrotta

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Se è stato usato il comando **Interrompi** del menu **Debug** per interrompere il programma ma la chiamata di MFC è stata comunque eseguita, è possibile usare la finestra Stack di chiamate per tornare alla funzione, dopo aver verificato che il problema dipende dal codice. Per altre informazioni, vedere [procedura: usare la finestra stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Talvolta è possibile che il codice si interrompa nel message pump. In questo caso, non è disponibile codice utente nello stack di chiamate. Per evitare questo problema, usare i punti di interruzione (se possibile con condizioni e conteggi dei passaggi) anziché il comando **Interrompi**. Per altre informazioni, vedere [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Passare alla funzione da cui è stato chiamato MFC

- Utilizzare la finestra **stack di chiamate** .

## <a name="see-also"></a>Vedi anche

- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)