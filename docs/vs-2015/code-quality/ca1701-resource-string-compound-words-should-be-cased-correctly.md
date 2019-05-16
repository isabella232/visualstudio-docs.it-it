---
title: 'CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38d8195baa540c2c212c71938b6266e28df49101
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683057"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Category|Microsoft.Naming|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Una stringa di risorsa contiene una parola composta non sembra essere digitati correttamente.

## <a name="rule-description"></a>Descrizione della regola
 Ogni parola nella stringa di risorsa è suddivisa in token basati sulle maiuscole e minuscole. Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft. Se riconosciuta, la parola produce una violazione della regola. Sono esempi di parole composte che causano una violazione "CheckSum" e "MultiPart", che devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, molte eccezioni vengono compilate nella regola e sono contrassegnate molte parole singole, ad esempio "Toolbar" e "Filename", che deve essere digitati due parole distinte. In questo esempio verranno contrassegnate "ToolBar" e "FileName".

 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare la parola in modo che viene maiuscole e minuscole.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografici e l'intento consiste nell'usare due parole.

 È anche possibile aggiungere le parole composte in un dizionario personalizzato per il correttore ortografico. Parole del dizionario personalizzato non causano le violazioni. Per altre informazioni, vedere [Procedura: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regole correlate
 [CA1702: Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche
 [Convenzioni di maiuscole/minuscole](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [linee guida sulla denominazione](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
