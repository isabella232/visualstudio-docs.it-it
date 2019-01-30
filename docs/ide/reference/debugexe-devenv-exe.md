---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93a582af62ed0eac8cdc0f5da55ac7bda555152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008972"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Apre il file eseguibile specificato per il debug.

## <a name="syntax"></a>Sintassi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argomenti

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