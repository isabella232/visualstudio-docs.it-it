---
title: Comando Stampa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662150"
---
# <a name="print-command"></a>Comando Print
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Valuta un'espressione o visualizza il testo specificato.

## <a name="syntax"></a>Sintassi

```
Debug.Print text
```

## <a name="arguments"></a>Argomenti
 `text` Obbligatorio. Espressione da valutare o testo da visualizzare.

## <a name="remarks"></a>Osservazioni
 È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando

```
>Debug.Print expA
```

 può anche essere scritto

```
>? expA
```

 Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.

## <a name="example"></a>Esempio

```
>Debug.Print varA
```

## <a name="see-also"></a>Vedere anche
 [Istruzione Evaluate comando](../../ide/reference/evaluate-statement-command.md) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra di comando](../../ide/reference/command-window.md) [Trova/comando casella](../../ide/find-command-box.md) di comando [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
