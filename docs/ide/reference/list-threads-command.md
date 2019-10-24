---
title: Comando Elenca thread
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c89f4e38d21e7dd66f53b8e768019a3e53c7a39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747882"
---
# <a name="list-threads-command"></a>Comando Elenca thread
Visualizza un elenco dei thread del programma corrente.

## <a name="syntax"></a>Sintassi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>argomenti
`index`

Parametro facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.

## <a name="remarks"></a>Note
Quando specificato, l'argomento `index` contrassegna il thread indicato come thread corrente. Nell'elenco viene visualizzato un asterisco (*) accanto al thread corrente.

## <a name="example"></a>Esempio

```
>Debug.ListThreads
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)