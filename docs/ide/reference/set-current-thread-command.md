---
title: Comando Imposta thread corrente
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d782a507d57e459aa5735cf34717f13e41d4cde
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "72748609"
---
# <a name="set-current-thread-command"></a>Comando Imposta thread corrente
Imposta il thread specificato come thread corrente.

## <a name="syntax"></a>Sintassi

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argomenti
`index`

Obbligatorio. Seleziona un thread in base al relativo indice.

## <a name="example"></a>Esempio

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Vedere anche

- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)