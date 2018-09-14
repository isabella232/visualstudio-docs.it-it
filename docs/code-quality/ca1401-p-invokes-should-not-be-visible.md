---
title: 'CA1401: I P-Invoke non devono essere visibili'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c1d4d9cc5e1550dee87609e5ef0e99dcd9d0cf5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548626"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: I P/Invoke non devono essere visibili

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta i <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo (implementato anche dal `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Descrizione della regola
 I metodi contrassegnati con il <xref:System.Runtime.InteropServices.DllImportAttribute> attributo (o i metodi che vengono definiti usando il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) usare Platform Invocation Services per accedere al codice non gestito. Questi metodi non devono essere esposti. Mantenendo i metodi privati o interni, è assicurarsi che la libreria non può essere utilizzata da una violazione di sicurezza consentendo ai chiamanti di accedere alle API non gestite che non è stato possibile chiamare in caso contrario.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il livello di accesso del metodo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente dichiara un metodo che violano questa regola.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]