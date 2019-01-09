---
title: Comando Watch
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccc9c6af2a87502c2b651e91f7d935ffc7ae3474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964481"
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

## <a name="remarks"></a>Note
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