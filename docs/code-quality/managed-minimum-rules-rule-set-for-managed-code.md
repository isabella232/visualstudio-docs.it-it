---
title: Set di regole minime gestite per codice gestito
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c929abe75a22e705cc86f256dbbf7942280149d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013288"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Set di regole minime gestite per codice gestito

Le regole minime gestite concentrare l'attenzione sui problemi più critici del codice, incluse potenziali lacune nella protezione, arresti anomali delle applicazioni e altri errori importanti per la logica e progettazione. Includere questo set di regole nel set di regole personalizzati creati per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi Disposable devono essere Disposable|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi eliminabili devono essere eliminati|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|
