---
title: Eseguire il debug delle violazioni di accesso quando si esegue l'app all'esterno Visual Studio
titleSuffix: ''
description: Usare il debugger JUST-IN-TIME per eseguire il debug di una violazione di accesso che si verifica all'esterno Visual Studio ambiente.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ec9b41f45211294f0587d4e78fc879394e677e7f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080819"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Come è possibile eseguire il debug di violazioni di accesso quando si esegue un programma fuori dal debugger?

## <a name="problem-description"></a>Descrizione del problema
 Il programma viene eseguito correttamente nell'ambiente di Visual Studio, ma quando viene eseguito autonomamente con il sistema operativo Windows, genera una violazione di accesso. Come è possibile effettuare il debug di questo problema?

## <a name="solution"></a>Soluzione
 Impostare l'opzione [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) ed eseguire il programma autonomamente finché non si verifica la violazione di accesso. Nella finestra di dialogo **Violazione di accesso** sarà quindi possibile fare clic su **Annulla** per avviare il debugger.

## <a name="see-also"></a>Vedi anche
- [Domande frequenti sul debug di codice nativo](../debugger/debugging-native-code-faqs.md)
- [Debug del codice nativo](../debugger/debugging-native-code.md)