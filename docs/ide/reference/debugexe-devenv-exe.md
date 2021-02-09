---
title: -DebugExe (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando DebugExe devenv per aprire un file eseguibile specifico di cui eseguire il debug.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894608"
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

## <a name="remarks"></a>Commenti

Le stringhe che seguono il parametro *ExecutableFile* vengono passate a tale file come argomenti.

## <a name="example"></a>Esempio

Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
