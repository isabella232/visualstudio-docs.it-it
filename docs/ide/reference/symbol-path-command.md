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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3792f3d6f86faf0b58e8cf8f1b76984ba3bd5d80
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926002"
---
# <a name="symbol-path-command"></a>Comando Percorso simboli
Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.

## <a name="syntax"></a>Sintassi

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Argomenti
`pathname`

facoltativo. Elenco di percorsi delimitato da punti e virgola usato dal debugger per la ricerca dei simboli.

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
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)