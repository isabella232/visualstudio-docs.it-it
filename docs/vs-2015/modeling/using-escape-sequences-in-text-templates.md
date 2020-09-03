---
title: Utilizzo di sequenze di escape in modelli di testo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659426"
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilizzo di sequenze di escape in modelli di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Procedura: generare modelli da modelli utilizzando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
