---
title: Comando Imposta/Rimuovi punto di interruzione
description: Informazioni su come usare il comando Attiva/Disattiva punto di interruzione per attivare o disattivare il punto di interruzione, a seconda dello stato corrente, nella posizione corrente nel file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0404840f5aa1859c058391c7398f7c2d1fcd86fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628566"
---
# <a name="toggle-breakpoint-command"></a>Comando Imposta/Rimuovi punto di interruzione
Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.

## <a name="syntax"></a>Sintassi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argomenti

`text`\
facoltativo. Se il testo viene specificato, la riga viene contrassegnata come punto di interruzione con nome. In caso contrario, la riga viene contrassegnata come punto di interruzione senza nome, analogamente a quanto accade quando si preme F9.

## <a name="example"></a>Esempio
Nell'esempio seguente il punto di interruzione corrente viene impostato/rimosso.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
