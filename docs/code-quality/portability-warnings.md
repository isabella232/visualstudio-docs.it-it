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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163076"
---
# <a name="portability-warnings"></a>avvisi di portabilità
Gli avvisi di portabilità supportano la portabilità tra diversi sistemi operativi.

## <a name="in-this-section"></a>In questa sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1900: I campi del tipo di valore devono essere portabili @ no__t-0|Questa regola consente di verificare che le strutture dichiarate tramite un attributo di layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 64 bit.|
|[CA1901: Le dichiarazioni P/Invoke devono essere portabili @ no__t-0|Questa regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che le relative dimensioni siano corrette quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 32 bit e a 64 bit.|
|[CA1903: Usare solo l'API del Framework di destinazione @ no__t-0|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|
