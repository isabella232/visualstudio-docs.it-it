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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0633c3e94a870117e1ae171903581da448b09ace
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227213"
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