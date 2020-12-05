---
title: Comando Avvia
description: Informazioni sul comando di avvio e sul modo in cui inizia il debug del progetto di avvio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d6d9e1e36a2790fb63f9d39c0c83d67d889cc0a8
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616421"
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

## <a name="remarks"></a>Commenti
Il comando **Avvia**, quando eseguito, esegue un'operazione RunToCursor sull'indirizzo specificato.

## <a name="example"></a>Esempio
In questo esempio viene avviato il debugger e le eccezioni vengono ignorate.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
