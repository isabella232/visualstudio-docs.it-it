---
title: Tornare alla funzione che ha chiamato MFC se interrotta | Microsoft Docs
description: Informazioni su come tornare alla funzione che ha chiamato MFC se l'esecuzione viene interrotta nel debugger di Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 751688b72a7603e76733906775c594cd28e78c28
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148949"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Procedura: tornare alla funzione che ha chiamato MFC se interrotta

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

Se è stato usato il comando **Interrompi** del menu **Debug** per interrompere il programma ma la chiamata di MFC è stata comunque eseguita, è possibile usare la finestra Stack di chiamate per tornare alla funzione, dopo aver verificato che il problema dipende dal codice. Per altre informazioni, vedere [procedura: usare la finestra stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

Talvolta è possibile che il codice si interrompa nel message pump. In questo caso, non è disponibile codice utente nello stack di chiamate. Per evitare questo problema, usare i punti di interruzione (se possibile con condizioni e conteggi dei passaggi) anziché il comando **Interrompi**. Per altre informazioni, vedere [Breakpoints and Tracepoints](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Passare alla funzione da cui è stato chiamato MFC

- Utilizzare la finestra **stack di chiamate** .

## <a name="see-also"></a>Vedere anche

- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)