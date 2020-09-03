---
title: 'CA2105: i campi di matrici non devono essere di sola lettura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: db52bf869642a5bdcc28eeb0792b295ae314a508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538671"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: I campi di matrici non devono essere di sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo pubblico o protetto che include una matrice è dichiarato di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 Quando si applica il `readonly` `ReadOnly` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] modificatore (in) a un campo contenente una matrice, il campo non può essere modificato per fare riferimento a una matrice diversa. È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura. Il codice che prende decisioni o esegue operazioni basate sugli elementi di una matrice di sola lettura a cui è possibile accedere pubblicamente potrebbe contenere una vulnerabilità di sicurezza sfruttabile.

 Si noti che la presenza di un campo pubblico viola anche la regola di progettazione [CA1051: non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere la vulnerabilità di sicurezza identificata da questa regola, non basarsi sul contenuto di una matrice di sola lettura a cui è possibile accedere pubblicamente. Si consiglia vivamente di utilizzare una delle procedure seguenti:

- Sostituire la matrice con una raccolta fortemente tipizzata che non può essere modificata. Per altre informazioni, vedere <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Sostituire il campo public con un metodo che restituisce un clone di una matrice privata. Poiché il codice non si basa sul clone, non vi sono pericoli se gli elementi vengono modificati.

  Se si sceglie il secondo approccio, non sostituire il campo con una proprietà; le proprietà che restituiscono matrici compromettono negativamente le prestazioni. Per ulteriori informazioni, vedere [CA1819: le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 L'esclusione di un avviso da questa regola è fortemente sconsigliata. Non si verificano praticamente scenari in cui il contenuto di un campo di sola lettura non è importante. In tal caso, rimuovere il `readonly` modificatore anziché escludere il messaggio.

## <a name="example"></a>Esempio
 Questo esempio illustra i rischi derivanti dalla violazione di questa regola. La prima parte Mostra una libreria di esempio con un tipo, `MyClassWithReadOnlyArrayField` , che contiene due campi ( `grades` e `privateGrades` ) che non sono sicuri. Il campo `grades` è pubblico e pertanto vulnerabile a qualsiasi chiamante. Il campo `privateGrades` è privato, ma è ancora vulnerabile perché viene restituito ai chiamanti dal `GetPrivateGrades` metodo. Il `securePrivateGrades` campo viene esposto in modo sicuro dal `GetSecurePrivateGrades` metodo. Viene dichiarata come privata per seguire buone procedure di progettazione. La seconda parte Mostra il codice che modifica i valori archiviati `grades` nei `privateGrades` membri e.

 Nell'esempio seguente viene visualizzata la libreria di classi di esempio.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Esempio
 Il codice seguente usa la libreria di classi di esempio per illustrare i problemi di sicurezza della matrice di sola lettura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 L'output di questo esempio è:

 **Prima di manomissione: gradi: 90, 90, 90 voti privati: 90, 90, 90 voti sicuri, 90, 90, 90** 
 **Dopo la manomissione: gradi: 90, 555, 90 voti privati: 90, 555, 90 voti sicuri, 90, 90, 90**
## <a name="see-also"></a>Vedere anche
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
