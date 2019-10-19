---
title: Comando Espressioni di controllo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604825"
---
# <a name="watch-command"></a>Comando Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.

## <a name="syntax"></a>Sintassi

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argomenti
 `index` Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.

## <a name="remarks"></a>Osservazioni
 `index` deve essere di tipo Integer. I valori validi sono 1, 2, 3 e 4.

## <a name="example"></a>Esempio

```
>Debug.Watch1
```

## <a name="see-also"></a>Vedere anche
 [Finestre auto e variabili locali](../../debugger/autos-and-locals-windows.md) [procedura: modificare un valore in una finestra delle variabili](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [procedura: usare la finestra di dialogo controllo immediato finestra di dialogo](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra di comando](../../ide/reference/command-window.md) [Trova/comando casella](../../ide/find-command-box.md) di comando [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
