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
ms.openlocfilehash: 065648588b51ad6c71ae1a10235da4f096470abe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Apre il file eseguibile specificato per il debug.

## <a name="syntax"></a>Sintassi

```
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

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)