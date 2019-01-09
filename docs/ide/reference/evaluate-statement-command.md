---
title: Comando Valuta istruzione
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0be6e57c0c741420006d20c0945b9b8c8b77d51
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864125"
---
# <a name="evaluate-statement-command"></a>Comando Valuta istruzione
Valuta e visualizza l'istruzione specificata.

## <a name="syntax"></a>Sintassi

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argomenti
 `text` Obbligatorio. Istruzione da valutare.

## <a name="remarks"></a>Note
 La finestra usata per immettere il comando **EvaluateStatement** determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.

 Nella finestra **Comando** il segno di uguale (=) viene interpretato come operatore di confronto. Pertanto, se ad esempio i valori delle variabili `a` e `b` sono diversi, il comando

```cmd
>Debug.EvaluateStatement(a=b)
```

 restituisce il valore `false`.

 Al contrario, nella finestra **Controllo immediato** il segno di uguale (=) viene interpretato come operatore di assegnazione. Il comando

```cmd
>Debug.EvaluateStatement(a=b)
```

 assegna ad esempio alla variabile `a` il valore della variabile `b`.

## <a name="example"></a>Esempio

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Vedere anche

- [Comando Stampa](../../ide/reference/print-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)