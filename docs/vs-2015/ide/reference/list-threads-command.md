---
title: Comando Elenca thread | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671144"
---
# <a name="list-threads-command"></a>Comando Elenca thread
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza un elenco dei thread del programma corrente.

## <a name="syntax"></a>Sintassi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argomenti
 `index` Facoltativo. Seleziona un thread in base al relativo indice e lo contrassegna come thread corrente.

## <a name="remarks"></a>Osservazioni
 Quando specificato, l'argomento `index` contrassegna il thread indicato come thread corrente. Nell'elenco viene visualizzato un asterisco (*) accanto al thread corrente.

## <a name="example"></a>Esempio

```
>Debug.ListThreads
```

## <a name="see-also"></a>Vedere anche
 [Elencare stack di chiamate](../../ide/reference/list-call-stack-command.md) [elenco comandi Disassembly comando](../../ide/reference/list-disassembly-command.md) [Visual Studio comandi](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando](../../ide/find-command-box.md) [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
