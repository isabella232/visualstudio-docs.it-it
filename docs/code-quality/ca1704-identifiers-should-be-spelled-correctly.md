---
title: 'CA1704: Gli identificatori devono essere digitati correttamente'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa04ca237134c1947b5c58b921f87f32a1ecfb16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234299"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Gli identificatori devono essere digitati correttamente

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft. Questa regola non controlla i costruttori o i membri con nome speciale, ad esempio le funzioni di accesso get e set Property.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza l'identificatore in token e controlla l'ortografia di ogni token. L'algoritmo di analisi esegue le trasformazioni seguenti:

- Le lettere maiuscole avviano un nuovo token. Ad esempio, MyNameIsJoe suddivide in token a "My", "Name", "is", "Joe".

- Per più lettere maiuscole, l'ultima lettera maiuscola avvia un nuovo token. Ad esempio, GUIEditor suddivide in token in "GUI", "Editor".

- Gli apostrofi iniziali e finali vengono rimossi. Ad esempio, "sender" suddivide in token in "sender".

- I caratteri di sottolineatura indicano la fine di un token e vengono rimossi. Ad esempio, hello_world suddivide in token su "Hello", "World".

- Le e commerciali incorporate vengono rimosse. Ad esempio, per & Mat suddivide in token in "Format".

## <a name="language"></a>Linguaggio

Il controllo ortografico attualmente controlla solo i dizionari delle impostazioni cultura in lingua inglese. È possibile modificare le impostazioni cultura del progetto nel file di progetto aggiungendo l'elemento **CodeAnalysisCulture** .

Ad esempio:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se si impostano le impostazioni cultura su un valore diverso da una lingua inglese, questa regola di analisi del codice viene disabilitata automaticamente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola a un dizionario personalizzato.

### <a name="to-add-words-to-a-custom-dictionary"></a>Per aggiungere parole a un dizionario personalizzato

Denominare il file XML del dizionario personalizzato *CustomDictionary. XML*. Inserire il dizionario nella directory di installazione dello strumento, nella directory del progetto o nella directory associata allo strumento sotto il profilo dell'utente ( *%USERPROFILE%\Application\\data...* ). Per informazioni su come aggiungere il dizionario personalizzato a un progetto in Visual Studio, vedere [procedura: Personalizzare il dizionario](../code-quality/how-to-customize-the-code-analysis-dictionary.md)di analisi del codice.

- Aggiungere parole che non devono causare una violazione nel percorso dizionario/parole/riconoscimento.

- Aggiungere parole che dovrebbero provocare una violazione sotto il percorso dizionario/parole/non riconosciuto.

- Aggiungere parole che devono essere contrassegnate come obsolete sotto il percorso dizionario/parole/deprecato. Vedere l'argomento [relativo alle regole correlate CA1726: Per ulteriori informazioni](../code-quality/ca1726-use-preferred-terms.md) , utilizzare i termini preferiti.

- Aggiungere le eccezioni alle regole di maiuscole e minuscole dell'acronimo al percorso Dictionary/Acronims/CasingExceptions.

Di seguito è riportato un esempio della struttura di un file di dizionario personalizzato:

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola solo se la parola è intenzionalmente digitata in modo errato e la parola viene applicata a un set limitato di librerie. Le parole con ortografia corretta riducono la curva di apprendimento necessaria per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA2204: I valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703 Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709 Gli identificatori devono essere configurati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708 Gli identificatori devono differire più di case](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Usa termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
