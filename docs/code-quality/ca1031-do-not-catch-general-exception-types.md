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
ms.openlocfilehash: e9746119c746679817076c86e3d5a9080cec30d9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744691"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Non rilevare tipi di eccezione generali

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un'eccezione, ad esempio <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> si trova in un `catch` istruzione o una clausola catch generale, ad esempio `catch()` viene usato.

## <a name="rule-description"></a>Descrizione della regola
 Le eccezioni generali non devono essere rilevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rilevare un'eccezione più specifica oppure generare nuovamente l'eccezione generale come ultima istruzione nel `catch` blocco.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Il rilevamento di tipi di eccezione generali problemi in fase di esecuzione da parte dell'utente della libreria possono essere nascosti e può rendere più difficile il debug.

> [!NOTE]
> A partire da .NET Framework 4, common language runtime (CLR) non trasmette più eccezioni stato danneggiato che si verificano nel sistema operativo e codice gestito, ad esempio le violazioni di accesso nel [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], per essere gestito dal codice gestito. Se si desidera che da compilare un'applicazione in .NET Framework 4 o versioni successive e manutenzione la gestione delle eccezioni stato danneggiato, è possibile applicare il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al metodo che gestisce l'eccezione di stato danneggiato.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un tipo che viola la regola e un tipo che implementa correttamente il `catch` blocco.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA2200: Eseguire il rethrow per conservare i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)