---
title: Eseguire il debug delle violazioni di accesso quando si esegue l'app all'esterno di Visual Studio
titleSuffix: ''
description: Usare il debugger JIT per eseguire il debug di una violazione di accesso che si verifica all'esterno dell'ambiente di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49d1fb2b24488692031c647139aa1f1076f0dd6f
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398484"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?

## <a name="problem-description"></a>Descrizione del problema
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso. Come è possibile effettuare il debug di questo problema?

## <a name="solution"></a>Soluzione
 Impostare l'opzione [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) ed eseguire il programma autonomamente finché non si verifica la violazione di accesso. Nella finestra di dialogo **Violazione di accesso** sarà quindi possibile fare clic su **Annulla** per avviare il debugger.

## <a name="see-also"></a>Vedere anche
- [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)