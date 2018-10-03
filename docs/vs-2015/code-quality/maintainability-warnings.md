---
title: Avvisi di manutenibilità | Microsoft Docs
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
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 53e4763ecc4e9f36dd402f33bfad30e5795c1814
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525566"
---
# <a name="maintainability-warnings"></a>avvisi di manutenibilità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [avvisi di manutenibilità](https://docs.microsoft.com/visualstudio/code-quality/maintainability-warnings).  
  
Avvisi di manutenibilità supportano la manutenzione di libreria e applicazione.  
  
## <a name="in-this-section"></a>In questa sezione  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1500: I nomi delle variabili non devono corrispondere ai nomi dei campi](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un metodo di istanza dichiara un parametro o una variabile locale il cui nome corrisponde a un campo di istanza del tipo dichiarante, generando errori.|  
|[CA1501: Evitare ereditarietà eccessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà. Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione.|  
|[CA1502: Evitare complessità eccessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Questa regola misura il numero di percorsi linearmente indipendenti tramite il metodo, determinato dal numero e dalla complessità di rami condizionali.|  
|[CA1504: Controllare i nomi dei campi fuorvianti](../code-quality/ca1504-review-misleading-field-names.md)|Il nome di un campo di istanza inizia con "s _", o il nome di un valore statico (Shared in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) campo inizia con "m _".|  
|[CA1505: evitare codice non gestibile](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o metodo presenta un valore di indice di gestibilità basso. Un indice di manutenibilità basso indica che un tipo o un metodo è probabilmente difficile da gestire e sarebbe un buon candidato per la riprogettazione.|  
|[CA1506: Evitare un numero eccessivo di accoppiamenti di classi](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



