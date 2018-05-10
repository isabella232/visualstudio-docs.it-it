---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07dfcbb6064d0f1043c0621534b953a5f5c63e82
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Apre il file eseguibile specificato per il debug.

## <a name="syntax"></a>Sintassi

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argomenti
 `ExecutableFile`

 Obbligatorio. Percorso e nome di un file con estensione exe.

 Se il file con estensione exe non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato normalmente.

## <a name="remarks"></a>Note
 Le stringhe che seguono il parametro `ExecutableFile` vengono passate al file come argomenti.

## <a name="example"></a>Esempio
 Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)