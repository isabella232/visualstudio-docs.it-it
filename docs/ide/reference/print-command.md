---
title: Comando Print
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 2ef4f0c5c6bd5be2820e1f666529fc43fac59763
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
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
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)