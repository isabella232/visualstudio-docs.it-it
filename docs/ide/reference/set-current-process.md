---
title: Imposta processo corrente
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 907ef900283cb3f15d9e65f7196c3cf42e191ed3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="set-current-process"></a>Imposta processo corrente
Imposta il processo specificato come processo attivo nel debugger.

## <a name="syntax"></a>Sintassi

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argomenti
 `index`

 Obbligatorio. L'indice del processo.

## <a name="remarks"></a>Note
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.

## <a name="example"></a>Esempio

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)