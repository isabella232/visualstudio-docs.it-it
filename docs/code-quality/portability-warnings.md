---
title: avvisi di portabilità
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61efbc2022b2c0cd60e005936e148bbaf1d900a4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091730"
---
# <a name="portability-warnings"></a>avvisi di portabilità
Gli avvisi di portabilità supportano la portabilità tra diversi sistemi operativi.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900.md)|Questa regola consente di verificare che le strutture dichiarate tramite un attributo di layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 64 bit.|
|[CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901.md)|Questa regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che le relative dimensioni siano corrette quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 32 bit e a 64 bit.|
|[CA1903: Usare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|
