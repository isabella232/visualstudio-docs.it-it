---
title: Utilizzo di sequenze di escape in modelli di testo
description: Informazioni su come usare sequenze di escape nei modelli di testo per generare tag di modello di testo e usare caratteri di escape e virgolette di controllo solo nel codice C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: e5d77665ddc8f08a5efe2594fb41a8f7424e67b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033954"
---
# <a name="use-escape-sequences-in-text-templates"></a>Usare sequenze di escape nei modelli di testo

È possibile usare sequenze di escape nei modelli di testo per generare tag di modello di testo e (solo nel codice C#) per eseguire l'escape dei caratteri di controllo e delle virgolette.

Per stampare i tag di apertura e chiusura per un blocco di codice standard nel file di output, eseguire l'escape dei tag come indicato di seguito:

```
\<# ... \#>
```

È possibile eseguire la stessa operazione con altre direttive del modello di testo e tag del blocco di codice.

Se un blocco di testo include stringhe usate per eseguire l'escape dei tag del modello di testo, è possibile usare le sequenze di escape seguenti:

- Se un tag del modello di testo è preceduto da un numero pari di caratteri di escape ( ), il parser del modello includerà metà dei caratteri di escape e includerà la sequenza come tag del modello \\ di testo. Ad esempio, se il modello di testo contiene quattro caratteri di escape, nel file generato saranno presenti due \\ caratteri " "" .

- Se il tag del modello di testo è preceduto da un numero dispari di caratteri di escape ( ), il parser del modello includerà metà dei caratteri " " più il \\ \\ tag stesso ( \<# or #> ). Il tag non è considerato un tag modello di testo.

- Se un carattere di escape ( ) viene visualizzato altrove in qualsiasi sequenza diversa da dove viene utilizzato un carattere di controllo o una virgoletta (solo in C#), il carattere verrà \\ restituito direttamente.

## <a name="see-also"></a>Vedi anche

- [Procedura: generare modelli da modelli utilizzando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
