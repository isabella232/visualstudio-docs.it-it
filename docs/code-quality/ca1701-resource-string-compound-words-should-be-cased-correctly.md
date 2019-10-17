---
title: 'CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d7aa3c29ca8ba82f6c50b070c5210cf10d1884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443924"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Category|Microsoft. Naming|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Una stringa di risorsa contiene una parola composta che non sembra essere inclusa correttamente nel caso.

## <a name="rule-description"></a>Descrizione della regola

Ogni parola nella stringa di risorsa viene suddivisa in token basati sulla combinazione di maiuscole e minuscole. Ogni combinazione di due token contigui viene controllata in base alla libreria del correttore ortografico Microsoft. Se riconosciuta, la parola produce una violazione della regola. Esempi di parole composte che causano una violazione sono "CheckSum" e "MultiPart", che devono essere considerati come "checksum" e "multipart", rispettivamente. A causa dell'utilizzo comune precedente, vengono compilate diverse eccezioni nella regola e vengono contrassegnate diverse parole, ad esempio "barra degli strumenti" e "nomefile", che devono essere racchiuse tra due parole distinte. In questo esempio, la barra degli strumenti e il nome del file verranno contrassegnati.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare la parola in modo che sia configurata correttamente.

## <a name="change-the-dictionary-language"></a>Modificare la lingua del dizionario

Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Se si desidera modificare la lingua del correttore ortografico, è possibile aggiungere uno degli attributi seguenti al file *AssemblyInfo.cs* o *AssemblyInfo. vb* :

- Usare <xref:System.Reflection.AssemblyCultureAttribute> per specificare le impostazioni cultura se le risorse si trovano in un assembly satellite.
- Usare <xref:System.Resources.NeutralResourcesLanguageAttribute> per specificare le *impostazioni cultura non associate ad alcun paese* dell'assembly se le risorse si trovano nello stesso assembly del codice.

> [!IMPORTANT]
> Se si impostano le impostazioni cultura su un valore diverso da una lingua inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografico e l'intento è usare due parole.

È anche possibile aggiungere parole composte a un dizionario personalizzato per il correttore ortografico. Le parole nel dizionario personalizzato non causano alcuna violazione. Per altre informazioni, vedere [procedura: personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regole correlate

- [CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche

- [Convenzioni per l'uso di maiuscole e minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)
