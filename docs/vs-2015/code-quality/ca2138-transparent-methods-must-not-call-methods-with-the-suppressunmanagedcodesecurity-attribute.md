---
title: "CA2138: i metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 65e00d319bff3bbfd3c441c6b60ed8a703e69251
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654808"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente per la sicurezza chiama un metodo contrassegnato con l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata su qualsiasi metodo trasparente che chiama direttamente nel codice nativo, ad esempio tramite una chiamata P/Invoke (platform invoke). I metodi di interoperabilità P/Invoke e COM contrassegnati con l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> comportano l'esecuzione di un LinkDemand sul metodo chiamante. Poiché il codice trasparente per la sicurezza non è in grado di soddisfare I LinkDemand, il codice non può chiamare anche metodi contrassegnati con l'attributo SuppressUnmanagedCodeSecurity o metodi della classe contrassegnati con l'attributo SuppressUnmanagedCodeSecurity. Il metodo avrà esito negativo o la richiesta verrà convertita in una richiesta completa.

 Le violazioni di questa regola conducono a una <xref:System.MethodAccessException> nel modello di trasparenza della sicurezza di livello 2 e a una richiesta completa di <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l'attributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> e contrassegnare il metodo con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
