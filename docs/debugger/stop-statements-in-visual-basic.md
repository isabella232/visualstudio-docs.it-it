---
title: Istruzioni Stop in Visual Basic | Microsoft Docs
description: Esaminare l'istruzione Visual Basic stop, che fornisce un'alternativa a livello di codice per l'impostazione di un punto di interruzione in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a17aafd508acd9272e8058ea7ca3ff585a8c0c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904940"
---
# <a name="stop-statements-in-visual-basic"></a>Istruzioni Stop in Visual Basic

L'istruzione Stop di Visual Basic fornisce un'alternativa a livello di codice all'impostazione di un punto di interruzione. Quando il debugger rileva un'istruzione Stop, viene interrotta l'esecuzione del programma, ossia viene attivata la modalità di interruzione. I programmatori C# possono ottenere lo stesso effetto usando una chiamata a <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Per impostare o rimuovere un'istruzione Stop, è necessario modificare il codice sorgente. Le istruzioni Stop non possono essere impostate né rimosse mediante i comandi del debugger, come invece avviene per i punti di interruzione.

A differenza di un'istruzione End, l'istruzione Stop non reimposta le variabili né consente di tornare alla modalità di progettazione. Per continuare l'esecuzione dell'applicazione, scegliere Continua dal menu Debug.

Quando si esegue un'applicazione Visual Basic all'esterno del debugger, un'istruzione Stop avvia il debugger se è abilitato il debug JIT. Se il debug JIT non è abilitato, l'istruzione Stop si comporta come se fosse un'istruzione End e termina l'esecuzione. Poiché non si verificherà alcun evento QueryUnload o Unload, sarà necessario rimuovere tutte le istruzioni Stop dalla versione di rilascio dell'applicazione Visual Basic. Per altre informazioni, vedere [Debug JIT](just-in-time-debugging-in-visual-studio.md).

 Per evitare di dover rimuovere le istruzioni Stop, è possibile utilizzare la compilazione condizionale:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Un'altra alternativa consiste nell'usare un' <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> istruzione anziché l'istruzione Stop. Un' <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> istruzione interrompe l'esecuzione solo quando non viene soddisfatta una condizione specificata. <xref:System.Diagnostics.Debug.Assert%2A> le istruzioni vengono rimosse automaticamente quando si compila una versione di rilascio. Per ulteriori informazioni, vedere [asserzioni nel codice gestito](assertions-in-managed-code.md). Se si vuole <xref:System.Diagnostics.Debug.Assert%2A> che un'istruzione che interrompe sempre l'esecuzione nella versione di debug, è possibile eseguire questa operazione:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Tuttavia, un'altra alternativa consiste nell'usare il <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> Metodo:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](debugger-security.md)
- [Tipi di progetto C#, F# e Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debug del codice gestito](debugging-managed-code.md)
