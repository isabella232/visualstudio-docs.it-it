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
ms.openlocfilehash: 54630b7fba69ef96a2c08486e535ae45d8e614b8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234759"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: I tipi visibili a COM devono essere creabili

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft. interoperabilità|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo di riferimento che è contrassegnato in modo specifico come visibile a Component Object Model (COM) contiene un costruttore con parametri pubblico, ma non contiene un costruttore pubblico predefinito (senza parametri).

## <a name="rule-description"></a>Descrizione della regola
Non è possibile creare un tipo senza un costruttore predefinito pubblico da parte dei client COM. Tuttavia, il tipo è ancora accessibile ai client COM se è disponibile un altro metodo per creare il tipo e passarlo al client, ad esempio tramite il valore restituito di una chiamata al metodo.

La regola ignora i tipi derivati da <xref:System.Delegate?displayProperty=fullName>.

Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, aggiungere un costruttore predefinito pubblico o rimuovere <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> dal tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se vengono fornite altre modalità per creare e passare l'oggetto al client COM.

## <a name="related-rules"></a>Regole correlate
[CA1017 Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche

- [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)