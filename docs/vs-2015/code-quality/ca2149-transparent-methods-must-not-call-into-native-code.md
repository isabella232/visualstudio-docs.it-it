---
title: 'CA2149: I metodi Transparent non devono chiamare in codice nativo | Microsoft Docs'
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
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e048bd5e85388fcccf54a4a48d81acfb6cc66b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208832"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: I metodi Transparent non devono effettuare chiamate nel codice nativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo chiama una funzione nativa tramite uno stub del metodo, ad esempio P/Invoke.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su qualsiasi metodo trasparente che chiama direttamente in codice nativo, ad esempio, tramite P/Invoke. Le violazioni di questa regola conducono a un <xref:System.MethodAccessException> nel modello di trasparenza di livello 2 e una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, contrassegnare il metodo che chiama il codice nativo con il <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]



