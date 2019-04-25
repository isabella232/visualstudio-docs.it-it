---
title: Comando Watch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6965378151bb44db1024ac4e9a49de618f410dc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789000"
---
# <a name="watch-command"></a>Comando Watch
Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.

## <a name="syntax"></a>Sintassi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argomenti
 `index`

 Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.

## <a name="remarks"></a>Osservazioni
 `index` deve essere di tipo Integer. I valori validi sono 1, 2, 3 e 4.

## <a name="example"></a>Esempio

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Vedere anche

- [Finestre Auto e Variabili locali](../../debugger/autos-and-locals-windows.md)
- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md) (Impostare un'espressione di controllo per le variabili con le finestre Espressione di controllo e Controllo immediato in Visual Studio)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)