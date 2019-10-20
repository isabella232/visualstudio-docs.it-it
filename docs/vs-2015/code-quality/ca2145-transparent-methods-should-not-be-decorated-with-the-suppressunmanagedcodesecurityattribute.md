---
title: 'CA2145: i metodi Transparent non devono essere decorati con SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610214"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente, un metodo contrassegnato con il metodo <xref:System.Security.SecuritySafeCriticalAttribute> o un tipo che contiene un metodo è contrassegnato con l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Descrizione della regola
 I metodi decorati con l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> hanno un LinkDemand implicito situato su qualsiasi metodo che lo chiama. Questo LinkDemand richiede che il codice che effettua la chiamata sia critico per la sicurezza. Contrassegnando il metodo che utilizza SuppressUnmanagedCodeSecurity con l'attributo <xref:System.Security.SecurityCriticalAttribute>, questo requisito risulta più ovvio per i chiamanti del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo o il tipo con l'attributo <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Comments
