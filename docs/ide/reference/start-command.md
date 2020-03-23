---
title: Comando Avvia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590280"
---
# <a name="start-command"></a>Comando Avvia
Inizia il debug del progetto di avvio.

## <a name="syntax"></a>Sintassi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argomenti
`address`

Facoltativa. Indirizzo in corrispondenza del quale il programma sospende l'esecuzione, simile a un punto di interruzione nel codice sorgente. Questo argomento è valido solo in modalità di debug.

## <a name="remarks"></a>Osservazioni
Il comando **Avvia**, quando eseguito, esegue un'operazione RunToCursor sull'indirizzo specificato.

## <a name="example"></a>Esempio
In questo esempio viene avviato il debugger e le eccezioni vengono ignorate.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Vedere anche

- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
