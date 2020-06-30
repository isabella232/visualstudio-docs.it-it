---
title: 'CA2211: i campi non costanti non devono essere visibili | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa67c33eac5d618c0a080323720775beea7b68c3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548213"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: I campi non costanti non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft. Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo statico pubblico o protetto non è costante né è di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 I campi statici che non sono costanti né in sola lettura non sono thread-safe. L'accesso a tale campo deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe. Poiché si tratta di competenze difficili da apprendere e da padroneggiare, il test di tale oggetto pone le proprie difficoltà, i campi statici vengono usati per archiviare i dati che non cambiano. Questa regola si applica alle librerie; le applicazioni non devono esporre alcun campo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere costante il campo statico o di sola lettura. Se ciò non è possibile, riprogettare il tipo in modo da usare un meccanismo alternativo, ad esempio una proprietà thread-safe che gestisce l'accesso thread-safe al campo sottostante. Tenere presente che problemi quali i conflitti di blocco e i deadlock potrebbero influire sulle prestazioni e sul comportamento della libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si sta sviluppando un'applicazione e pertanto si ha il controllo completo sull'accesso al tipo che contiene il campo statico. Le finestre di progettazione della libreria non devono eliminare un avviso da questa regola. l'uso di campi statici non costanti può rendere difficile l'uso della libreria per gli sviluppatori.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
