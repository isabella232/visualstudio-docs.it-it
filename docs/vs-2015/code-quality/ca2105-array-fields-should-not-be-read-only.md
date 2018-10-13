---
title: 'CA2105: I campi di matrici non devono essere sola lettura | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a310957f1552e289993643d39965d8a6a8693fe2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207948"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: I campi di matrici non devono essere di sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo pubblico o protetto che contiene una matrice viene dichiarato di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 Quando si applica il `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) modificatore a un campo che contiene una matrice, il campo non può essere modificato per fare riferimento a una matrice diversa. È tuttavia possibile modificare gli elementi della matrice archiviati in un campo in sola lettura. Il codice che prende decisioni o esegue le operazioni che si basano sugli elementi di una matrice di sola lettura che è possibile accedere pubblicamente potrebbe contenere una vulnerabilità di sicurezza sfruttabili.

 Si noti che anche la presenza di un campo pubblico viola la regola di progettazione [CA1051: non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per risolvere le vulnerabilità di sicurezza che è identificato da questa regola, non fare affidamento sul contenuto di una matrice di sola lettura che sono accessibili pubblicamente. È consigliabile usare una delle procedure riportate di seguito:

-   Sostituire la matrice con una raccolta fortemente tipizzata che non può essere modificata. Per altre informazioni, vedere <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Sostituire il campo pubblico con un metodo che restituisce un clone di una matrice privata. Poiché il codice non richiede il clone, non vi è alcun rischio se gli elementi vengono modificati.

 Se si sceglie il secondo approccio, non sostituire il campo con una proprietà. le proprietà che restituiscono matrici influisce negativamente sulle prestazioni. Per altre informazioni, vedere [CA1819: le proprietà non devono restituire matrici](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Esclusione di un avviso da questa regola è fortemente sconsigliato. Quasi non esistono scenari in cui il contenuto di un campo di sola lettura non sia importante. Se questo è il caso con lo scenario, rimuovere il `readonly` modificatore invece di escludere il messaggio.

## <a name="example"></a>Esempio
 In questo esempio vengono illustrati i rischi di violazione di questa regola. La prima parte illustra una libreria di esempio con un tipo `MyClassWithReadOnlyArrayField`, che contiene due campi (`grades` e `privateGrades`) che non sono sicure. Il campo `grades` è pubblico e pertanto vulnerabile a un chiamante qualsiasi. Il campo `privateGrades` è privato, ma è comunque vulnerabili perché viene restituita per i chiamanti dal `GetPrivateGrades` (metodo). Il `securePrivateGrades` campo viene esposto in modo sicuro dal `GetSecurePrivateGrades` (metodo). È dichiarato come private seguire migliori pratiche di progettazione. La seconda parte illustra il codice che modifica i valori archiviati nel `grades` e `privateGrades` membri.

 Nell'esempio seguente viene visualizzata la libreria di classi di esempio.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Esempio
 Il codice seguente usa la libreria di classi di esempio per illustrare i problemi di sicurezza di matrice di sola lettura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 L'output da questo esempio è:

 **Prima di manomissione: dei voti: 90, 90, 90 gradi privato: 90, 90, 90 gradi Secure, 90, 90, 90**
**dopo eventuali manomissioni: dei voti: 90, 555, 90 gradi privato: 90, 555, 90 gradi Secure, 90, 90, 90**
## <a name="see-also"></a>Vedere anche
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



