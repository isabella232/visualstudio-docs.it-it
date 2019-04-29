---
title: 'CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545932"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Category|Microsoft.Naming|
|Modifica importante|Rilievo-when generato su assembly.<br /><br /> Non sostanziale - Quando viene attivato su parametri di tipo.|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene più parole, fra cui almeno una che sembra essere composta e digitata in modo non corretto con distinzione tra maiuscole e minuscole.

## <a name="rule-description"></a>Descrizione della regola

Il nome dell'identificatore è suddiviso in parole che si basano le maiuscole e minuscole. Ogni combinazione di due parole contigui viene controllata dalla libreria del correttore ortografico Microsoft. Se è riconosciuta, l'identificatore genera una violazione della regola. Sono esempi di parole composte che causano una violazione "CheckSum" e "MultiPart", che devono essere digitati "Checksum" e "Multipart", rispettivamente. A causa di uso comune precedente, numerose eccezioni sono incorporate nella regola, e sono contrassegnate molte parole singole, ad esempio "Toolbar" e "Filename", che devono essere digitati due parole di distinte (in questo caso, "ToolBar" e "FileName").

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare il nome in modo che viene maiuscole e minuscole.

## <a name="language"></a>Linguaggio

Il correttore ortografico attualmente verifica solo a dizionari le impostazioni cultura basate su inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto, aggiungendo il **CodeAnalysisCulture** elemento.

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si imposta le impostazioni cultura su un valore qualsiasi diverso da una cultura basata su inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se entrambe le parti della parola composta sono riconosciute dal dizionario ortografici e l'intento consiste nell'usare due parole.

## <a name="related-rules"></a>Regole correlate

- [CA1701: Le parole composte di stringa di risorsa devono essere digitate correttamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Vedere anche

- [Convenzioni di denominazione](/dotnet/standard/design-guidelines/naming-guidelines)
- [Convenzioni per l'uso di maiuscole e minuscole](/dotnet/standard/design-guidelines/capitalization-conventions)