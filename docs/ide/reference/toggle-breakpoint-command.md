---
title: Comando Imposta/Rimuovi punto di interruzione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597321"
---
# <a name="toggle-breakpoint-command"></a>Comando Imposta/Rimuovi punto di interruzione
Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.

## <a name="syntax"></a>Sintassi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argomenti

`text`\
facoltativo. Se il testo viene specificato, la riga viene contrassegnata come punto di interruzione con nome. In caso contrario, la riga viene contrassegnata come punto di interruzione senza nome, analogamente a quanto accade quando si preme F9.

## <a name="example"></a>Esempio
Nell'esempio seguente il punto di interruzione corrente viene impostato/rimosso.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
