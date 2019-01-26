---
title: Utilizzo di sequenze di escape in modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: a4b88786c8403347e6526a7a097afcee69889b2a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031093"
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilizzo di sequenze di escape in modelli di testo
Nei modelli di testo per generare tag di modello di testo e (in c# solo codice), è possibile usare le sequenze di escape per virgolette doppie e caratteri di escape di controllo.

 Per stampare i tag di aperti e chiusura per un blocco di codice standard per il file di output, escape i tag come indicato di seguito:

```
\<# ... \#>
```

 È possibile eseguire la stessa con altri tag blocco direttiva e il codice del modello di testo.

 Se un blocco di testo include le stringhe utilizzate per eseguire l'escape di tag di modello di testo, è possibile usare le sequenze di escape seguenti:

-   Se un tag di modello di testo è preceduto da un numero pari di escape (\\) il modello di caratteri parser verrà includono la metà dei caratteri di escape e includono la sequenza come un tag di modello di testo. Ad esempio, se sono presenti quattro caratteri di escape nel modello di testo, esisterà due "\\" caratteri nel file generato.

-   Se il tag di modello di testo è preceduto da un numero dispari di escape (\\) caratteri, il parser del modello includerà la metà del "\\" caratteri oltre il tag stesso (\<# o #>). Il tag non è considerato come un tag di modello di testo.

-   Se un carattere di escape (\\) carattere viene visualizzato ovunque in qualsiasi sequenza diverso da in cui viene eseguito l'escape un carattere di controllo o una virgoletta (solo in c#), verranno restituiti i caratteri direttamente.

## <a name="see-also"></a>Vedere anche

- [Procedura: Generare modelli da modelli utilizzando le sequenze di Escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)