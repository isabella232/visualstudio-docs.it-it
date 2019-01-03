---
title: 'CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2cc74bb7d3cc15e593d465a8c8d0d55275954ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841781"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente

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

## <a name="change-the-dictionary-language"></a>Modificare la lingua di dizionario

Per impostazione predefinita, viene utilizzata la versione inglese (en) del correttore ortografico. Se si desidera modificare la lingua del correttore ortografico, è possibile farlo mediante l'aggiunta di uno dei seguenti attributi per il *AssemblyInfo.cs* oppure *AssemblyInfo* file:

- Usare <xref:System.Reflection.AssemblyCultureAttribute> specificare le impostazioni cultura, se le risorse si trovano in un assembly satellite.
- Uso <xref:System.Resources.NeutralResourcesLanguageAttribute> per specificare il *delle impostazioni cultura neutre* dell'assembly se le risorse sono nello stesso assembly del codice.

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore qualsiasi diverso da una cultura basata su inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografici e l'intento consiste nell'usare due parole.

È anche possibile aggiungere le parole composte in un dizionario personalizzato per il correttore ortografico. Parole del dizionario personalizzato non causano le violazioni. Per altre informazioni, vedere [Procedura: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Regole correlate

- [CA1702: LE Le parole composte devono essere digitate correttamente](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche

- [Convenzioni per l'uso di maiuscole e minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)