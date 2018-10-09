---
title: Common Language Runtime e valutazione delle espressioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e5a896609d4dc28fb3b320f6d71f0b02b705229
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525514"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e valutazione delle espressioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Common Language Runtime e valutazione delle espressioni](https://docs.microsoft.com/visualstudio/extensibility/debugger/common-language-runtime-and-expression-evaluation).  
  
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compilatori, ad esempio Visual Basic e c# (pronunciato C-sharp), destinate a Common Language Runtime (CLR), produrre linguaggio MSIL (Microsoft Intermediate), ovvero successive compilate in codice nativo. CLR fornisce un motore di debug (DE) per il debug del codice risulta. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di compilare in codice MSIL e pertanto non sarà necessario scrivere il proprio DE. Tuttavia, è necessario scrivere un analizzatore di espressioni (EE) che è in grado di valutazione di espressioni all'interno del contesto del linguaggio di programmazione.  
  
## <a name="discussion"></a>Discussione  
 Le espressioni del linguaggio computer vengono in genere analizzate per produrre un set di oggetti dati e un set di operatori usato per la manipolazione. L'espressione "A + B" può essere analizzata per applicare l'operatore di addizione (+) per i dati degli oggetti, ad esempio, "A" e "B", determinando in un altro oggetto dati. Set totale di oggetti dati, operatori e le relative associazioni sono spesso rappresentati in un programma come un albero, con gli operatori ai nodi dell'albero e gli oggetti dati nelle filiali. Un'espressione che è stato suddiviso in forma di struttura ad albero viene spesso definita una struttura ad albero analizzato.  
  
 Una volta che un'espressione è stata analizzata, viene chiamato un provider di simboli (SP) per valutare ogni oggetto dati. Se, ad esempio, "A" è definito sia in più di un metodo, quindi la domanda "Quale A?" deve essere una risposta prima che è possibile ottenere il valore dell'oggetto. La risposta restituita dalla stored procedure è simile a "Il terzo elemento sullo stack frame quinto" o "A 50 byte oltre l'inizio della memoria statica allocato a questo metodo".  
  
 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono inoltre generare informazioni di debug molto descrittive che viene scritto in un file di DataBase di programma (PDB). Fino a quando un compilatore di linguaggio di tua proprietà produce informazioni di debug nello stesso formato i compilatori CLR, SP di CLR è in grado di identificare che del linguaggio denominato oggetti dati. Dopo aver individuato un oggetto dati con nome, l'analizzatore di Espressioni Usa un oggetto strumento di associazione per associare l'oggetto dati (o associare) nell'area di memoria che contiene il valore di tale oggetto. Il DE possa quindi ottenere o impostare un nuovo valore per l'oggetto dati.  
  
 Un compilatore proprietario può fornire informazioni di debug tramite la chiamata di CLR i `ISymbolWriter` interface (definito in .NET Framework nello spazio dei nomi `System.Diagnostics.SymbolStore`). La compilazione in codice MSIL e scrivendo le informazioni di debug tramite queste interfacce, è possibile usare un compilatore proprietario il CLR Germania e provider di servizi. Questo semplifica notevolmente l'integrazione di un linguaggio proprietario nell'IDE di Visual Studio.  
  
 Quando la Germania CLR chiama l'analizzatore di Espressioni proprietarie per valutare un'espressione, la Germania fornisce l'analizzatore di Espressioni con le interfacce per un Service Pack e un oggetto strumento di associazione. Di conseguenza, la scrittura di un mezzo del motore di debug basata su CLR è necessario solo implementare le interfacce dell'analizzatore di espressione appropriata. Common Language Runtime si occupa dell'associazione e il simbolo di gestione per l'utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
