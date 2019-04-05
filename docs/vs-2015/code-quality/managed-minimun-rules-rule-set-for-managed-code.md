---
title: Set di regole minime gestite per codice gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fbbbdf8a1ece9a57d0216a6c9b59ac9d2a8ea474
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955683"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Set di regole minime gestite per codice gestito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le regole minime gestite concentrare l'attenzione sui problemi più critici del codice, incluse potenziali lacune nella protezione, arresti anomali delle applicazioni e altri errori importanti per la logica e progettazione. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi Disposable devono essere Disposable|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi eliminabili devono essere eliminati|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|
