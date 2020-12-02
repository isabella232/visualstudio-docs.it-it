---
title: Comando Watch
description: Informazioni sul comando Watch e sul modo in cui crea e apre un'istanza specificata di un finestra Espressioni di controllo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631c9cf61e6da70b3c7554a1aac0cacc8eef0294
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480148"
---
# <a name="watch-command"></a>Comando Watch
Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.

## <a name="syntax"></a>Sintassi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argomenti

`index`\
Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.

## <a name="remarks"></a>Commenti

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
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
