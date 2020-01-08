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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569205"
---
# <a name="go-to-command"></a>Comando Vai a
Sposta il cursore sulla riga specificata.

## <a name="syntax"></a>Sintassi

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argomenti
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
- [Command Window](../../ide/reference/command-window.md) (Finestra di comando)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
