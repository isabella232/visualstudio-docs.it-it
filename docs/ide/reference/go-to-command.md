---
title: Comando Vai a
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93ad14561b1fdd2aade1978831b784e014568a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668255"
---
# <a name="go-to-command"></a>Comando Vai a
Sposta il cursore sulla riga specificata.

## <a name="syntax"></a>Sintassi

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>argomenti
`linenumber`\
Parametro facoltativo. Valore integer che rappresenta il numero della riga a cui passare.

## <a name="remarks"></a>Note
La numerazione delle righe inizia da uno. Se il valore di `linenumber` è minore di uno, viene visualizzata la prima riga. Se il valore di `linenumber` è maggiore del numero dell'ultima riga, viene visualizzata l'ultima riga.

Se non viene specificato alcun un valore per `linenumber`, viene visualizzata la finestra di dialogo **Vai alla riga**.

L'alias per questo comando è GoToLn.

## <a name="example"></a>Esempio

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)