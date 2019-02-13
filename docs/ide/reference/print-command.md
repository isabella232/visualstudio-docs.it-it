---
title: Comando Print
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9a3de1fba86c78f16703efd858448bc0f25e8d0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952294"
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