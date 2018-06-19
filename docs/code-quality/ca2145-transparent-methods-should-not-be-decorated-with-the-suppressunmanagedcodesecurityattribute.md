---
title: 'CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 06ea700534bfb5306699409cde22bad2177f67b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918935"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute
|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente, un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> metodo o un tipo che contiene un metodo è contrassegnato con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 I metodi decorati con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo presentano un LinkDemand implicito su ogni metodo che lo chiama. Questo LinkDemand richiede che il codice che effettua la chiamata sia critico per la sicurezza. Contrassegnare il metodo che utilizza SuppressUnmanagedCodeSecurity con il <xref:System.Security.SecurityCriticalAttribute> attributo rende più ovvio questo requisito per i chiamanti del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo o il tipo con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]

### <a name="comments"></a>Commenti