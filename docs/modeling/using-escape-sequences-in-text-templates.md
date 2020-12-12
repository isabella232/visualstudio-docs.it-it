---
title: Utilizzo di sequenze di escape in modelli di testo
description: Informazioni su come usare sequenze di escape nei modelli di testo per generare tag di modello di testo e per eseguire il escape di caratteri di controllo e virgolette solo nel codice C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b007a9b5ccf41a27cda7d9833064eb60394c4dc
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361326"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usare sequenze di escape in modelli di testo

È possibile usare le sequenze di escape nei modelli di testo per generare tag di modello di testo e (solo in codice C#) per caratteri di escape e virgolette.

Per stampare i tag di apertura e chiusura per un blocco di codice standard nel file di output, eseguire il escape dei tag come segue:

```
\<# ... \#>
```

È possibile eseguire la stessa operazione con altri tag del blocco di codice e di direttiva del modello di testo.

Se un blocco di testo include stringhe usate per l'escape dei tag del modello di testo, è possibile usare le sequenze di escape seguenti:

- Se un tag del modello di testo è preceduto da un numero pari di caratteri di escape ( \\ ), il parser del modello includerà la metà dei caratteri di escape e includerà la sequenza come tag del modello di testo. Se, ad esempio, nel modello di testo sono presenti quattro caratteri di escape, saranno presenti due \\ caratteri "" nel file generato.

- Se il tag del modello di testo è preceduto da un numero dispari di caratteri di escape ( \\ ), il parser del modello includerà la metà dei \\ caratteri "" più il tag stesso ( \<# or #> ). Il tag non è considerato un tag di modello di testo.

- Se un \\ carattere di escape () viene visualizzato in qualsiasi altra sequenza diversa da quella in cui viene sottoposto a escape da un carattere di controllo o da un'offerta (solo in C#), il carattere verrà restituito direttamente.

## <a name="see-also"></a>Vedi anche

- [Procedura: generare modelli da modelli utilizzando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
