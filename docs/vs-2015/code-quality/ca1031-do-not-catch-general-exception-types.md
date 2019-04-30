---
title: 'CA1031: Non rilevare tipi di eccezione generale | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4588a949b4b6439c3f76270b0bcdab9cd52c23d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431221"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Non rilevare tipi di eccezione generali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il rilevamento di tipi di eccezione generali problemi in fase di esecuzione da parte dell'utente della libreria possono essere nascosti e può rendere più difficile il debug.

> [!NOTE]
> Inizia con la [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], common language runtime (CLR) non trasmette più eccezioni stato danneggiato che si verificano nel sistema operativo e codice gestito, ad esempio le violazioni di accesso nel [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], per essere gestito dal codice gestito. Se si vuole compilare un'applicazione nel [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o versioni successive e mantenere la gestione delle eccezioni stato danneggiato, è possibile applicare il <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al metodo che gestisce l'eccezione di stato danneggiato.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un tipo che viola la regola e un tipo che implementa correttamente il `catch` blocco.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2200: Eseguire il rethrow per conservare i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
