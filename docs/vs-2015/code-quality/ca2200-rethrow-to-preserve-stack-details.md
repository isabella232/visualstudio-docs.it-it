---
title: 'CA2200: rigenerazione per mantenere i dettagli dello stack | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546367"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Eseguire il rethrow per mantenere i dettagli dello stack
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Viene generata nuovamente un'eccezione e l'eccezione viene specificata in modo esplicito nell' `throw` istruzione.

## <a name="rule-description"></a>Descrizione della regola
 Una volta generata un'eccezione, parte delle informazioni che contiene è la traccia dello stack. La traccia dello stack è un elenco della gerarchia di chiamata del metodo che inizia con il metodo che genera l'eccezione e termina con il metodo che rileva l'eccezione. Se un'eccezione viene generata di nuovo specificando l'eccezione nell' `throw` istruzione, l'analisi dello stack viene riavviata nel metodo corrente e l'elenco di chiamate al metodo tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso. Per memorizzare le informazioni originali della traccia dello stack con l'eccezione, utilizzare l' `throw` istruzione senza specificare l'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, generare nuovamente l'eccezione senza specificare in modo esplicito l'eccezione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `CatchAndRethrowExplicitly` , che viola la regola e un metodo, `CatchAndRethrowImplicitly` , che soddisfa la regola.

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
