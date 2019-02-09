---
title: 'CA2112: I tipi protetti non devono esporre campi'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d46c9fe1b97b5bdfb081150a44aa69363eced53
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922797"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: I tipi protetti non devono esporre campi

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto contiene campi pubblici e protetta da un [richieste di collegamento](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descrizione della regola
 Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare i campi non pubblici e aggiungere i metodi che restituiscono i dati del campo o proprietà pubbliche. Controlli di sicurezza LinkDemand su tipi di proteggono l'accesso a proprietà e metodi del tipo. Sicurezza dall'accesso di codice, tuttavia, non si applica ai campi.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Per problemi di sicurezza sia per una progettazione ottimale, è necessario correggere le violazioni, rendendo non pubblici campi pubblici. È possibile eliminare un avviso da questa regola se il campo non contiene informazioni che devono rimanere protette e non fare affidamento sul contenuto del campo.

## <a name="example"></a>Esempio
 Nell'esempio seguente è costituito da una libreria di tipi (`SecuredTypeWithFields`) con i campi non protetti, un tipo (`Distributor`) consente di creare istanze del tipo di libreria e passate erroneamente istanze di tipi di autorizzazioni insufficienti per crearli e il codice dell'applicazione può leggere i campi di un'istanza anche se non dispone dell'autorizzazione che protegge il tipo.

 Il codice di libreria seguente viola la regola.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Esempio 1
 L'applicazione non è possibile creare un'istanza a causa la richiesta di collegamento che consente di proteggere il tipo protetto. La classe seguente consente all'applicazione ottenere un'istanza del tipo protetto.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Esempio 2
 L'applicazione riportata di seguito viene illustrato come fare, senza l'autorizzazione per accedere ai metodi del tipo protetta, accessibile dal codice relativi campi.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Questo esempio produce il seguente output:

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Regole correlate

- [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vedere anche

- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)