---
title: Comando Percorso simboli
description: Informazioni sul comando percorso simboli e su come imposta l'elenco di directory in cui il debugger deve cercare i simboli.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bd3268f3c40736f85a18b35e33c6cc78c96d6c88
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616447"
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

## <a name="remarks"></a>Commenti
Se non viene specificato un `pathname`, il comando elenca i percorsi dei simboli correnti.

## <a name="example-1"></a>Esempio 1
In questo esempio vengono aggiunti due percorsi all'elenco delle directory dei simboli.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>Esempio 2
In questo esempio viene visualizzato un elenco delimitato da punti e virgola dei percorsi dei simboli correnti.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Vedere anche

- [Finestra di comando](../../ide/reference/command-window.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
