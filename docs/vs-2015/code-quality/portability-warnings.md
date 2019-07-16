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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8f195f2219cfa2c81b24a3e04ddc559dc98a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142215"
---
# <a name="portability-warnings"></a>avvisi di portabilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avvisi di portabilità supportano la portabilità tra sistemi operativi diversi.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1900: I campi di tipo di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola verifica che le strutture dichiarate utilizzando un attributo di layout esplicito vengano allineate correttamente quando il marshalling nel codice non gestito nei sistemi operativi a 64 bit.|  
|[CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Questa regola restituisce le dimensioni di ogni parametro e il valore restituito di P/Invoke e verifica che la dimensione sia corretta durante il marshalling nel codice non gestito nei sistemi operativi a 32 e 64 bit.|  
|[CA1903: Usare l'API solo framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|
