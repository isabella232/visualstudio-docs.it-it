---
title: Debug.Print
description: Informazioni sul comando Print e sul modo in cui valuta un'espressione o Visualizza il testo specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0524ce015ea4675254615c11e5768e59049c37f6
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304135"
---
# <a name="print-command"></a>Stampa (comando)

Valuta un'espressione o visualizza il testo specificato.

## <a name="syntax"></a>Sintassi

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argomenti

`text`

Obbligatorio. Espressione da valutare o testo da visualizzare.

## <a name="remarks"></a>Commenti

È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando

```cmd
>Debug.Print expA
```

può anche essere scritto come

```cmd
? expA
```

Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.

## <a name="example"></a>Esempio

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Vedere anche

- [Comando valuta istruzione](../../ide/reference/evaluate-statement-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
