---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889410"
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