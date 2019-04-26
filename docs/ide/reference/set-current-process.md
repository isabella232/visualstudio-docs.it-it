---
title: Imposta processo corrente
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24f4c08147f72168f5207418a51d7a9cfa8a2b51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934562"
---
# <a name="set-current-process"></a>Imposta processo corrente
Imposta il processo specificato come processo attivo nel debugger.

## <a name="syntax"></a>Sintassi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argomenti
 `index`

 Obbligatorio. L'indice del processo.

## <a name="remarks"></a>Osservazioni
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.

## <a name="example"></a>Esempio

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)