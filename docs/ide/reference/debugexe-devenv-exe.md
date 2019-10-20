---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661672"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Apre il file eseguibile specificato per il debug.

## <a name="syntax"></a>Sintassi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>argomenti

- *ExecutableFile*

  Obbligatorio. Percorso e nome di un file con estensione `.exe`. Se il file `.exe` non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e Visual Studio viene avviato normalmente.

## <a name="remarks"></a>Note

Le stringhe che seguono il parametro *ExecutableFile* vengono passate a tale file come argomenti.

## <a name="example"></a>Esempio

Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)