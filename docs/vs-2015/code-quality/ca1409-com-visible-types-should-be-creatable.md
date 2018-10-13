---
title: 'CA1409: I tipi visibili a Com devono essere creabili | Microsoft Docs'
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
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2aa50d16f0661b3c4baa40fae24fbee24f6fa7bd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200317"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: I tipi visibili a COM devono essere creabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se sono disponibili altri modi per creare e passare l'oggetto per il client COM.

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Qualificazione di tipi .NET per l'interoperatività](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



