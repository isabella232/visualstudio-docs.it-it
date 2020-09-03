---
title: Utilizzo di sequenze di escape in modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83e6e5cf163037077d0517e5f7ea460f9124f27c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594045"
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

## <a name="see-also"></a>Vedere anche

- [Procedura: generare modelli da modelli utilizzando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
