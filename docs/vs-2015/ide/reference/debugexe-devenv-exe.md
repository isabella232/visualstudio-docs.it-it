---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660797"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Apre il file eseguibile specificato per il debug.

## <a name="syntax"></a>Sintassi

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argomenti
 `ExecutableFile` Obbligatorio. Percorso e nome di un file con estensione exe.

 Se il file con estensione exe non viene trovato o non esiste, non viene visualizzato alcun avviso o errore e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene avviato normalmente.

## <a name="remarks"></a>Osservazioni
 Le stringhe che seguono il parametro `ExecutableFile` vengono passate al file come argomenti.

## <a name="example"></a>Esempio
 Nell'esempio seguente il file `MyApplication.exe` viene aperto per il debug.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
