---
title: 'CA1701: le parole composte della stringa di risorsa devono essere corrette correttamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669262"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Category|Microsoft. Naming|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Una stringa di risorsa contiene una parola composta che non sembra essere inclusa correttamente nel caso.

## <a name="rule-description"></a>Descrizione della regola
 Ogni parola nella stringa di risorsa viene suddivisa in token basati sulla combinazione di maiuscole e minuscole. Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft. Se riconosciuta, la parola produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", che devono essere considerati come "checksum" e "multipart", rispettivamente. A causa dell'utilizzo comune precedente, vengono compilate diverse eccezioni nella regola e vengono contrassegnate diverse parole, ad esempio "barra degli strumenti" e "nomefile", che devono essere racchiuse tra due parole distinte. In questo esempio, la barra degli strumenti e il nome del file verranno contrassegnati.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Modificare la parola in modo che sia configurata correttamente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografico e l'intento è usare due parole.

 È anche possibile aggiungere parole composte a un dizionario personalizzato per il correttore ortografico. Le parole nel dizionario personalizzato non causano alcuna violazione. Per altre informazioni, vedere [procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regole correlate
 [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche
 [Linee guida](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) per la denominazione delle [convenzioni di maiuscole](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
