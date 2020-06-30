---
title: 'CA1409: i tipi visibili a com devono essere creabili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547329"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: I tipi visibili a COM devono essere creabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo di riferimento che è contrassegnato in modo specifico come visibile a Component Object Model (COM) contiene un costruttore con parametri pubblico, ma non contiene un costruttore pubblico predefinito (senza parametri).

## <a name="rule-description"></a>Descrizione della regola
 Non è possibile creare un tipo senza un costruttore predefinito pubblico da parte dei client COM. Tuttavia, il tipo è ancora accessibile ai client COM se è disponibile un altro metodo per creare il tipo e passarlo al client, ad esempio tramite il valore restituito di una chiamata al metodo.

 La regola ignora i tipi derivati da <xref:System.Delegate?displayProperty=fullName> .

 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere un costruttore predefinito pubblico o rimuovere <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> dal tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se vengono fornite altre modalità per creare e passare l'oggetto al client COM.

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Qualificazione di tipi .NET per](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) l'interoperatività [interoperabilità con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
