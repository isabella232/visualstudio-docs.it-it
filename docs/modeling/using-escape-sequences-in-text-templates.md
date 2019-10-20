---
title: Utilizzo di sequenze di escape in modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662924"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usare sequenze di escape in modelli di testo

È possibile utilizzare sequenze di escape nei modelli di testo per generare tag di modello di testo C# e (solo in codice) per caratteri di escape e virgolette.

Per stampare i tag di apertura e chiusura per un blocco di codice standard nel file di output, eseguire il escape dei tag come segue:

```
\<# ... \#>
```

È possibile eseguire la stessa operazione con altri tag del blocco di codice e di direttiva del modello di testo.

Se un blocco di testo include stringhe usate per l'escape dei tag del modello di testo, è possibile usare le sequenze di escape seguenti:

- Se un tag del modello di testo è preceduto da un numero pari di caratteri di escape (\\), il parser del modello includerà la metà dei caratteri di escape e includerà la sequenza come tag del modello di testo. Se, ad esempio, nel modello di testo sono presenti quattro caratteri di escape, saranno presenti due caratteri "\\" nel file generato.

- Se il tag del modello di testo è preceduto da un numero dispari di caratteri di escape (\\), il parser del modello includerà la metà dei caratteri "\\" più il tag stesso (\< # o # >). Il tag non è considerato un tag di modello di testo.

- Se un carattere di escape (\\) viene visualizzato in qualsiasi altra sequenza diversa da quella in cui viene sottoposto a escape da un carattere C# di controllo o da un'offerta (solo in), il carattere verrà restituito direttamente.

## <a name="see-also"></a>Vedere anche

- [Procedura: Generare modelli da modelli usando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)