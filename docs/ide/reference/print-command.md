---
title: Debug.Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567840"
---
# <a name="print-command"></a>Comando Print

Valuta un'espressione o visualizza il testo specificato.

## <a name="syntax"></a>Sintassi

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argomenti

`text`

Obbligatorio. Espressione da valutare o testo da visualizzare.

## <a name="remarks"></a>Osservazioni

È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando

```cmd
>Debug.Print expA
```

può anche essere scritto come

```cmd
? expA
```

Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.

## <a name="example"></a>Esempio

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Vedere anche

- [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
