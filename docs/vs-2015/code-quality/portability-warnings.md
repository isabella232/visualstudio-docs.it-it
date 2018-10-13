---
title: Avvisi di portabilità | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 3b7c38f8380fc8e52707b9c4817880b1ce86b4b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173082"
---
# <a name="portability-warnings"></a>avvisi di portabilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avvisi di portabilità supportano la portabilità tra sistemi operativi diversi.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola verifica che le strutture dichiarate utilizzando un attributo di layout esplicito vengano allineate correttamente quando il marshalling nel codice non gestito nei sistemi operativi a 64 bit.|  
|[CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Questa regola restituisce le dimensioni di ogni parametro e il valore restituito di P/Invoke e verifica che la dimensione sia corretta durante il marshalling nel codice non gestito nei sistemi operativi a 32 e 64 bit.|  
|[CA1903: Usare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|



