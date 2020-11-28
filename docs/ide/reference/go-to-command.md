---
title: Comando Vai a
description: Informazioni sul comando Vai a e sul modo in cui sposta il cursore nella riga specificata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305209"
---
# <a name="go-to-command"></a>Comando Vai a
Sposta il cursore sulla riga specificata.

## <a name="syntax"></a>Sintassi

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argomenti
`linenumber`\
facoltativo. Valore integer che rappresenta il numero della riga a cui passare.

## <a name="remarks"></a>Commenti
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
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
