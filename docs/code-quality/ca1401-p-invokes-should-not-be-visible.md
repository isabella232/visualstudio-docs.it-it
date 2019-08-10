---
title: 'CA1401: I P/Invoke non devono essere visibili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e26daf68e0031358605427b310bb7284d43baf1b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922142"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: I P/Invoke non devono essere visibili

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un metodo pubblico o protetto in un tipo pubblico dispone dell' <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo, anch ' esso implementato `Declare` dalla parola [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]chiave in.

## <a name="rule-description"></a>Descrizione della regola
I metodi contrassegnati con l' <xref:System.Runtime.InteropServices.DllImportAttribute> attributo (o i metodi definiti tramite la parola chiave in) utilizzano i `Declare` servizi di chiamata della [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]piattaforma per accedere al codice non gestito. Questi metodi non devono essere esposti. Mantenendo questi metodi privati o interni, assicurarsi che la libreria non possa essere usata per violare la sicurezza consentendo ai chiamanti di accedere alle API non gestite che non possono chiamare in altro modo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare il livello di accesso del metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene dichiarato un metodo che viola questa regola.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]