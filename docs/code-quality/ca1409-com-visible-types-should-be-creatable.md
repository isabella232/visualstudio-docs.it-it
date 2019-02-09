---
title: 'CA1409: I tipi visibili a COM devono essere creabili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05dbe964a16f838088fe8b053d59c1916daf38f7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933721"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: I tipi visibili a COM devono essere creabili

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo di riferimento contrassegnato specificatamente come visibile al modello COM (Component Object) contiene un costruttore con parametri pubblico ma non contiene un costruttore predefinito pubblico (senza parametri).

## <a name="rule-description"></a>Descrizione della regola
 Un tipo senza un costruttore predefinito pubblico non è possibile creare per i client COM. Tuttavia, il tipo comunque accessibili da parte dei client COM se è disponibile un altro mezzo per creare il tipo e passarlo al client (ad esempio, tramite il valore restituito di una chiamata al metodo).

 La regola ignora sempre i tipi derivati da <xref:System.Delegate?displayProperty=fullName>.

 Per impostazione predefinita, sono visibili a COM seguente: assembly, i tipi pubblici, i membri di istanza pubblici nei tipi pubblici e tutti i membri dei tipi di valore pubblico.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un costruttore predefinito pubblico o rimuovere il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> dal tipo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se sono disponibili altri modi per creare e passare l'oggetto per il client COM.

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche

- [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)