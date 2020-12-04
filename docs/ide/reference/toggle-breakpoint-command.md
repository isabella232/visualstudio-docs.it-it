---
title: Comando Imposta/Rimuovi punto di interruzione
description: Informazioni su come usare il comando attiva/disattiva punto di interruzione per attivare o disattivare il punto di interruzione, a seconda dello stato corrente, nella posizione corrente del file.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65144271f91d518dd6649fa1e97fc627d1b0009
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560967"
---
# <a name="toggle-breakpoint-command"></a>Comando Imposta/Rimuovi punto di interruzione
Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.

## <a name="syntax"></a>Sintassi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argomenti

`text`\
Facoltativo. Se il testo viene specificato, la riga viene contrassegnata come punto di interruzione con nome. In caso contrario, la riga viene contrassegnata come punto di interruzione senza nome, analogamente a quanto accade quando si preme F9.

## <a name="example"></a>Esempio
Nell'esempio seguente il punto di interruzione corrente viene impostato/rimosso.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
