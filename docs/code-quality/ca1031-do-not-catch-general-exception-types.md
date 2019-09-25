---
title: 'CA1031: Non rilevare tipi di eccezione generali'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236059"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Non rilevare tipi di eccezione generali

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un' <xref:System.Exception?displayProperty=fullName> eccezione generale <xref:System.SystemException?displayProperty=fullName> ,ad`catch` esempio o, viene rilevata in un'istruzione oppure vieneutilizzataunaclausolacatchgenerale,adesempio.`catch()`

## <a name="rule-description"></a>Descrizione della regola
Le eccezioni generali non devono essere rilevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rilevare un'eccezione più specifica o rigenerare l'eccezione generale come ultima istruzione nel `catch` blocco.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Il rilevamento dei tipi di eccezione generali può nascondere problemi di run-time dall'utente della libreria e rendere più difficile il debug.

> [!NOTE]
> A partire da .NET Framework 4, il Common Language Runtime (CLR) non recapita più le eccezioni di stato danneggiate che si verificano nel sistema operativo e il codice gestito, ad [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]esempio le violazioni di accesso in, per essere gestite dal codice gestito. Se si desidera compilare un'applicazione in .NET Framework 4 o versioni successive e gestire le eccezioni di stato danneggiate, è possibile applicare l' <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attributo al metodo che gestisce l'eccezione di stato danneggiato.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che implementa correttamente il `catch` blocco.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2200 Rigenerazione per mantenere i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)