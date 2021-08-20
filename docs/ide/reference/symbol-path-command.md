---
title: Comando Percorso simboli
description: Informazioni sul comando Percorso simboli e su come imposta l'elenco di directory per il debugger per la ricerca di simboli.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 96258c0318098f7a7bb5abb5481192cc7808c7ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151002"
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

## <a name="see-also"></a>Vedi anche

- [Finestra di comando](../../ide/reference/command-window.md)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
