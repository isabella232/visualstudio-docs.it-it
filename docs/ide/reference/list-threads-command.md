---
title: Comando Elenca thread
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f4d8706b41448289e5e653ee431ba56fb7d957f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031500"
---
# <a name="list-threads-command"></a>Comando Elenca thread
Visualizza un elenco dei thread del programma corrente.

## <a name="syntax"></a>Sintassi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argomenti
 `index`

 Facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.

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
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)