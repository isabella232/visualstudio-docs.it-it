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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e88dc1318e29ddf35073b78218eb113fe8952aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769652"
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
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)