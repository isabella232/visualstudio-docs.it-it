---
title: Comando Print
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cf241ec0a9ff849b52761a241e84a15d287bb88
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="print-command"></a>Comando Print
Valuta un'espressione o visualizza il testo specificato.

## <a name="syntax"></a>Sintassi

```
Debug.Print text
```

## <a name="arguments"></a>Argomenti
 `text`

 Obbligatorio. Espressione da valutare o testo da visualizzare.

## <a name="remarks"></a>Note
 È possibile usare il punto interrogativo (?) come alias per questo comando. Il comando

```
>Debug.Print expA
```

 può anche essere scritto

```
>? expA
```

 Entrambe le versioni di questo comando restituiscono il valore corrente dell'espressione `expA`.

## <a name="example"></a>Esempio

```
>Debug.Print varA
```

## <a name="see-also"></a>Vedere anche

- [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)