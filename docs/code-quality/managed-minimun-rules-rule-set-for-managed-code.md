---
title: Gestito minimo set di regole per il codice gestito
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9803c5171cb15454e465253e410b3dc2f4e6215e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919052"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Gestito minimo set di regole per il codice gestito
Le regole minime gestite concentrarsi sui problemi più critici del codice, inclusi i potenziali problemi di sicurezza, arresti anomali delle applicazioni e altri errori di logica e di progettazione rilevanti. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.

|Regola|Descrizione|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi disposable devono essere disposable|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi Disposable devono essere eliminati.|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Overload dell'operatore è uguale all'override di ValueType. Equals|
