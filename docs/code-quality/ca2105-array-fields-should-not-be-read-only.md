---
title: 'CA2105: I campi di matrici non devono essere di sola lettura'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeadbd977b8c7d97af611a2054692a6071f21a36
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928920"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: I campi di matrici non devono essere di sola lettura

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un campo pubblico o protetto che contiene una matrice viene dichiarato di sola lettura.

## <a name="rule-description"></a>Descrizione della regola

Quando si applica il `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modificatore a un campo che contiene una matrice, il campo non può essere modificato per fare riferimento a una matrice diversa. È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura. Il codice che prende decisioni o esegue le operazioni che si basano sugli elementi di una matrice di sola lettura che è possibile accedere pubblicamente potrebbe contenere una vulnerabilità di sicurezza sfruttabili.

Si noti che anche la presenza di un campo pubblico viola la regola di progettazione [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per risolvere le vulnerabilità di sicurezza che è identificato da questa regola, non fare affidamento sul contenuto di una matrice di sola lettura che sono accessibili pubblicamente. È consigliabile usare una delle procedure riportate di seguito:

- Sostituire la matrice con una raccolta fortemente tipizzata che non può essere modificata. Per altre informazioni, vedere <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Sostituire il campo pubblico con un metodo che restituisce un clone di una matrice privata. Poiché il codice non richiede il clone, non vi è alcun rischio se gli elementi vengono modificati.

Se si sceglie il secondo approccio, non sostituire il campo con una proprietà. le proprietà che restituiscono matrici influisce negativamente sulle prestazioni. Per altre informazioni, vedere [CA1819: Proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Esclusione di un avviso da questa regola è fortemente sconsigliato. Quasi non esistono scenari in cui il contenuto di un campo di sola lettura non sia importante. Se questo è il caso con lo scenario, rimuovere il `readonly` modificatore invece di escludere il messaggio.

## <a name="example-1"></a>Esempio 1

In questo esempio vengono illustrati i rischi di violazione di questa regola. La prima parte illustra una libreria di esempio con un tipo `MyClassWithReadOnlyArrayField`, che contiene due campi (`grades` e `privateGrades`) che non sono sicure. Il campo `grades` è pubblico e pertanto vulnerabile a un chiamante qualsiasi. Il campo `privateGrades` è privato, ma è comunque vulnerabili perché viene restituita per i chiamanti dal `GetPrivateGrades` (metodo). Il `securePrivateGrades` campo viene esposto in modo sicuro dal `GetSecurePrivateGrades` (metodo). È dichiarato come private seguire migliori pratiche di progettazione. La seconda parte illustra il codice che modifica i valori archiviati nel `grades` e `privateGrades` membri.

Nell'esempio seguente viene visualizzata la libreria di classi di esempio.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Esempio 2

Il codice seguente usa la libreria di classi di esempio per illustrare i problemi di sicurezza di matrice di sola lettura.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

L'output da questo esempio è:

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>Vedere anche

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>