---
title: Comando Print
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31f604d6df45cb22d18401b5925867d5ab0e02b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900886"
---
# <a name="print-command"></a>Comando Print
Valuta un'espressione o visualizza il testo specificato.

## <a name="syntax"></a>Sintassi

```cmd
Debug.Print text
```

## <a name="arguments"></a>Argomenti
 `text`

 Obbligatorio. Espressione da valutare o testo da visualizzare.

## <a name="remarks"></a>Note
 È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando

```cmd
>Debug.Print expA
```

 può anche essere scritto

```cmd
>? expA
```

 Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.

## <a name="example"></a>Esempio

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>Vedere anche

- [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)