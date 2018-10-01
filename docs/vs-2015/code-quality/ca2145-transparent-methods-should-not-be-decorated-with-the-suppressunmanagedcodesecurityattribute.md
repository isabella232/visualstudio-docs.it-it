---
title: 'CA2145: I metodi Transparent non devono essere decorati con SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7dcb7d2596a03bc78eed7dc4c3a1455c91478b04
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "47590985"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2145: i metodi Transparent non devono essere decorati con SuppressUnmanagedCodeSecurityAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute).

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente, un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> metodo o un tipo che contiene un metodo è contrassegnato con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 I metodi decorati con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo presentano un LinkDemand implicito su ogni metodo che lo chiama. Questo LinkDemand richiede che il codice che effettua la chiamata sia critico per la sicurezza. Contrassegnare il metodo che usa SuppressUnmanagedCodeSecurity con il <xref:System.Security.SecurityCriticalAttribute> attributo rende più ovvio questo requisito per i chiamanti del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo o tipo con il <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Commenti



