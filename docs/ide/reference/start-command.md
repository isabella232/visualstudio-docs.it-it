---
title: Comando Avvia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1e5ade7d02882633504ac5615ee751b2533adde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="start-command"></a>Comando Avvia
Inizia il debug del progetto di avvio.

## <a name="syntax"></a>Sintassi

```
Debug.Start [address]
```

## <a name="arguments"></a>Argomenti
 `address`

 Facoltativo. Indirizzo in corrispondenza del quale il programma sospende l'esecuzione, simile a un punto di interruzione nel codice sorgente. Questo argomento è valido solo in modalità di debug.

## <a name="remarks"></a>Note
 Il comando **Avvia**, quando eseguito, esegue un'operazione RunToCursor sull'indirizzo specificato.

## <a name="example"></a>Esempio
 In questo esempio viene avviato il debugger e le eccezioni vengono ignorate.

```
>Debug.Start
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)