---
title: 'CA1031: non intercettare i tipi di eccezione generali | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661889"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Non rilevare tipi di eccezione generali
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un'eccezione generale, ad esempio <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName>, viene rilevata in un'istruzione `catch` oppure viene utilizzata una clausola catch generale, ad esempio `catch()`.

## <a name="rule-description"></a>Descrizione della regola
 Le eccezioni generali non devono essere rilevate.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rilevare un'eccezione più specifica o rigenerare l'eccezione generale come ultima istruzione nel blocco `catch`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il rilevamento dei tipi di eccezione generali può nascondere problemi di run-time dall'utente della libreria e rendere più difficile il debug.

> [!NOTE]
> A partire dalla [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], il Common Language Runtime (CLR) non recapita più le eccezioni di stato danneggiate che si verificano nel sistema operativo e nel codice gestito, ad esempio le violazioni di accesso in [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], per essere gestite dal codice gestito. Se si desidera compilare un'applicazione in [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o versioni successive e gestire le eccezioni di stato danneggiate, è possibile applicare l'attributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al metodo che gestisce l'eccezione di stato danneggiato.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che implementa correttamente il blocco `catch`.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2200: Eseguire il rethrow per mantenere i dettagli dello stack](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
