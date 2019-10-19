---
title: Imposta processo corrente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665473"
---
# <a name="set-current-process"></a>Imposta processo corrente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta il processo specificato come processo attivo nel debugger.

## <a name="syntax"></a>Sintassi

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argomenti
 `index` Obbligatorio. L'indice del processo.

## <a name="remarks"></a>Osservazioni
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.

## <a name="example"></a>Esempio

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra di comando](../../ide/reference/command-window.md) [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
