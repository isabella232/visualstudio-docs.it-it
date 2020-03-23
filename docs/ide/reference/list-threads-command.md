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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b36b8f4d9970d94eb83c47b59e85d01f932589
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595488"
---
# <a name="list-threads-command"></a>Comando Elenca thread
Visualizza un elenco dei thread del programma corrente.

## <a name="syntax"></a>Sintassi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argomenti
`index`

Facoltativa. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.

## <a name="remarks"></a>Osservazioni
Quando specificato, l'argomento `index` contrassegna il thread indicato come thread corrente. Nell'elenco viene visualizzato un asterisco (*) accanto al thread corrente.

## <a name="example"></a>Esempio

```
>Debug.ListThreads
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)
- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
