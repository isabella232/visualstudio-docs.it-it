---
title: 'CA1401: P-Invoke non deve essere visibili | Microsoft Docs'
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
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1b811f57a3939a026152e70babbf263244aed056
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211698"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: I P/Invoke non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta i <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo (implementato anche dal `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Descrizione della regola
 I metodi contrassegnati con il <xref:System.Runtime.InteropServices.DllImportAttribute> attributo (o i metodi che vengono definiti usando il `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) usare Platform Invocation Services per accedere al codice non gestito. Questi metodi non devono essere esposti. Mantenendo i metodi privati o interni, è assicurarsi che la libreria non può essere utilizzata da una violazione di sicurezza consentendo ai chiamanti di accedere alle API non gestite che non è stato possibile chiamare in caso contrario.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il livello di accesso del metodo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente dichiara un metodo che violano questa regola.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]



