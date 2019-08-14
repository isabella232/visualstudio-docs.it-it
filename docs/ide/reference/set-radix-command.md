---
title: Comando Imposta radice
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13341d8cb6a708f4e10f211bd47b79a75e1b6e2a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926033"
---
# <a name="set-radix-command"></a>Comando Imposta radice
Imposta o restituisce la base numerica usata per visualizzare i valori integer.

## <a name="syntax"></a>Sintassi

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argomenti
`10` o `16` o `hex` o `dec`

facoltativo. Indica un valore decimale (10 o dec) o esadecimale (16 o hex). Se un argomento viene omesso, viene restituito il valore della radice corrente.

## <a name="example"></a>Esempio
Nell'esempio che segue, l'ambiente viene impostato per la visualizzazione dei valori integer in formato esadecimale.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)