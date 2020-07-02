---
title: "CA2139: i metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 233e4366befd2a5a0d5690b14198ac13e2fcc957
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546484"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: I metodi Transparent non possono usare l'attributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente è contrassegnato con l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola attiva qualsiasi metodo trasparente e tenta di gestire un'eccezione che danneggia il processo tramite l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo. Un'eccezione che danneggia il processo è una classificazione di eccezione CLR versione 4,0 di eccezioni di questo tipo <xref:System.AccessViolationException> . L'attributo HandleProcessCorruptedStateExceptionsAttribute può essere usato solo dai metodi critici per la sicurezza e sarà ignorato se applicato a un metodo trasparente. Per gestire le eccezioni che danneggiano il processo, questo metodo deve diventare critico per la sicurezza o critico per la sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo o contrassegnare il metodo con l' <xref:System.Security.SecurityCriticalAttribute> attributo o <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 In questo esempio, un metodo trasparente è contrassegnato con l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo e non avrà esito positivo per la regola. Anche il metodo deve essere contrassegnato con l' <xref:System.Security.SecurityCriticalAttribute> attributo o <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]
