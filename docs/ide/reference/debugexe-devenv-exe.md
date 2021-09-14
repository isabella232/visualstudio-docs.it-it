---
title: -DebugExe (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando DebugExe devenv per aprire un file eseguibile specificato di cui eseguire il debug.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8c65427c3228697b4d9e0faa07943f6e5ba7cc29
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634420"
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
