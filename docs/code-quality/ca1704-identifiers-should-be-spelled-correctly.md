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
ms.openlocfilehash: 8dbfc8081f980b7b9e978da782f1627a88a716a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809408"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Gli identificatori devono essere digitati correttamente

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft. Questa regola non verificare i costruttori o membri denominati speciali, ad esempio get e set di funzioni di accesso a proprietà.

## <a name="rule-description"></a>Descrizione della regola

Questa regola analizza l'identificatore per i token e controlla l'ortografia di ogni token. Algoritmo di analisi esegue le trasformazioni seguenti:

- Lettere maiuscole avviare un nuovo token. Ad esempio, MyNameIsJoe suddivide in token "My", "Name", "Is", "Joe".

- Per più lettere maiuscole, l'ultima lettera maiuscola avvia un nuovo token. Ad esempio, GUIEditor suddivide in token di "Interfaccia utente grafica", "Editor".

- Vengono rimossi iniziali e finali apostrofi. Ad esempio, 'sender' suddivide in token "mittente".

- Caratteri di sottolineatura indicano la fine di un token e vengono rimossi. Ad esempio Hello_world suddivide in token di "Hello", "world".

- Le e commerciali incorporate vengono rimossi. Ad esempio, per & mat viene scomposto nel token "format".

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

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, correggere l'ortografia del termine o aggiungere la parola al dizionario personalizzato.

### <a name="to-add-words-to-a-custom-dictionary"></a>Per aggiungere termini al dizionario personalizzato

Denominare il file XML di dizionario personalizzato *DizionarioPersonale*. Inserire il dizionario nella directory di installazione dello strumento, nella directory del progetto o nella directory che è associata allo strumento sotto il profilo dell'utente (*%USERPROFILE%\Application dati\\...* ). Per informazioni su come aggiungere il dizionario personalizzato a un progetto in Visual Studio, vedere [come: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Aggiungere le parole che non dovrebbero provocare una violazione in un percorso Dictionary/parole/Recognized.

- Aggiungere le parole che devono causare una violazione in un percorso dizionario/parole/non riconosciuto.

- Aggiungere le parole che devono essere contrassegnate come obsoleta in un percorso dizionario/parole/deprecate. Vedere l'argomento di regola correlata [CA1726: Utilizzare termini Preferiti](../code-quality/ca1726-use-preferred-terms.md) per altre informazioni.

- Aggiungere le eccezioni alle regole di maiuscole e minuscole degli acronimi al percorso di dizionario/acronimi/CasingExceptions.

Di seguito è riportato un esempio della struttura di un file del dizionario personalizzato:

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

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare un avviso da questa regola solo se la parola è intenzionalmente con errori di ortografia e la parola si applica a un set limitato di libreria. Correttamente ortografia consente di ridurre la curva di apprendimento necessario per le nuove librerie software.

## <a name="related-rules"></a>Regole correlate

- [CA2204: Valori letterali devono essere digitati correttamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Gli identificatori devono essere digitati correttamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Gli identificatori devono differenziarsi minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Vedere anche

- [Procedura: Personalizzare il dizionario di analisi codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
