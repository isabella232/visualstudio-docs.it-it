---
title: Avvisi di portabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671161"
---
# <a name="portability-warnings"></a>Portability Warnings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli avvisi di portabilità supportano la portabilità tra diversi sistemi operativi.

## <a name="in-this-section"></a>Contenuto della sezione

|Regola|Descrizione|
|----------|-----------------|
|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola consente di verificare che le strutture dichiarate tramite un attributo di layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 64 bit.|
|[CA1901: le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Questa regola valuta la dimensione di ciascun parametro e il valore restituito di P/Invoke e verifica che le relative dimensioni siano corrette quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 32 bit e a 64 bit.|
|[CA1903: Usare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|
