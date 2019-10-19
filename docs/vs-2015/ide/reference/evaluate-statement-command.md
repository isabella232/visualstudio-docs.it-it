---
title: Comando Valuta istruzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657703"
---
# <a name="evaluate-statement-command"></a>Comando Valuta istruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Valuta e visualizza l'istruzione specificata.

## <a name="syntax"></a>Sintassi

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argomenti
 `text` Obbligatorio. Istruzione da valutare.

## <a name="remarks"></a>Osservazioni
 La finestra usata per immettere il comando **EvaluateStatement** determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.

 Nella finestra **Comando** il segno di uguale (=) viene interpretato come operatore di confronto. Pertanto, se ad esempio i valori delle variabili `a` e `b` sono diversi, il comando

```
>Debug.EvaluateStatement(a=b)
```

 restituisce il valore `false`.

 Al contrario, nella finestra **Controllo immediato** il segno di uguale (=) viene interpretato come operatore di assegnazione. Il comando

```
>Debug.EvaluateStatement(a=b)
```

 assegna ad esempio alla variabile `a` il valore della variabile `b`.

## <a name="example"></a>Esempio

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Vedere anche
 [Comando stampa](../../ide/reference/print-command.md) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra di comando](../../ide/reference/command-window.md) [Trova/comando casella](../../ide/find-command-box.md) di comando [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
