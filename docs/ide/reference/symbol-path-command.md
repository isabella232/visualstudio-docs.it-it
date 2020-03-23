---
title: Comando Percorso simboli
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589383"
---
# <a name="symbol-path-command"></a>Comando Percorso simboli
Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.

## <a name="syntax"></a>Sintassi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argomenti
`pathname`

Facoltativa. Elenco di percorsi delimitato da punti e virgola usato dal debugger per la ricerca dei simboli.

## <a name="remarks"></a>Osservazioni
Se non viene specificato un `pathname`, il comando elenca i percorsi dei simboli correnti.

## <a name="example"></a>Esempio
In questo esempio vengono aggiunti due percorsi all'elenco delle directory dei simboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Esempio
In questo esempio viene visualizzato un elenco delimitato da punti e virgola dei percorsi dei simboli correnti.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Vedere anche

- [Finestra di comando](../../ide/reference/command-window.md)
- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
