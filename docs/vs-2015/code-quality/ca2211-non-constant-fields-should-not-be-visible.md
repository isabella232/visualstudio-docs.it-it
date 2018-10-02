---
title: 'CA2211: I campi Non costanti non devono essere visibili | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d6ad55a49d335f5f776ba7b75f8006559e0eb38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590013"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: I campi non costanti non devono essere visibili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2211: i campi Non costanti non devono essere visibili](https://docs.microsoft.com/visualstudio/code-quality/ca2211-non-constant-fields-should-not-be-visible).

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Category|Microsoft.Usage|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un campo statico pubblico o protetto non costante né è di sola lettura.

## <a name="rule-description"></a>Descrizione della regola
 I campi statici che non sono costanti né in sola lettura non sono thread-safe. Accesso a tale campo deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe. Poiché si tratta di competenze difficili per individuare e database master e un oggetto di questo tipo di test presenta difficoltà, i campi statici sono più adatta per archiviare i dati che non cambiano. Questa regola vale per le librerie. le applicazioni non devono esporre tutti i campi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impostare il campo statico costante o di sola lettura. Se questo non è possibile, riprogettare il tipo per usare un meccanismo alternativo, ad esempio una proprietà di thread-safe che gestisce l'accesso thread-safe per il campo sottostante. Tenere presente che problemi quali la contesa dei blocchi e i deadlock possono influire sulle prestazioni e comportamento della libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si sviluppa un'applicazione e pertanto avere controllo completo sull'accesso per il tipo che contiene il campo statico. Progettazione di librerie dovrebbero eliminare un avviso da questa regola. utilizzo di campi statici non costante può rendere usando la libreria difficile per gli sviluppatori di usare correttamente.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



