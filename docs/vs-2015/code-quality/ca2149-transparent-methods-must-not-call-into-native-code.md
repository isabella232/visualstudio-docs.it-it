---
title: 'CA2149: i metodi Transparent non devono chiamare il codice nativo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c1e254ae7912efbb6773155ed834e54a1db1832
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546328"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: I metodi Transparent non devono effettuare chiamate nel codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo chiama una funzione nativa tramite uno stub di metodo, ad esempio P/Invoke.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su qualsiasi metodo trasparente che chiama direttamente in codice nativo, ad esempio, tramite P/Invoke. Le violazioni di questa regola conducono a <xref:System.MethodAccessException> nel modello di trasparenza di livello 2 e a una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo che chiama il codice nativo con <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo o.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]
