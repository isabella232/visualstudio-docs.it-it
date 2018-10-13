---
title: Utilizzo di sequenze di Escape in modelli di testo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: be273c8cf69094a640ea7210bdbdc50005841a49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296543"
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilizzo di sequenze di escape in modelli di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Procedura: Generare modelli da modelli usando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)



