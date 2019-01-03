---
title: Motore di debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db4874c842775c02fdf50d827aea7daaac008587
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836237"
---
# <a name="debug-engine"></a>Motore di debug
Un motore di debug (DE) funziona con l'interprete o sistema operativo per fornire servizi di debug, ad esempio valutazione dell'espressione di controllo e i punti di interruzione esecuzione. La Germania è responsabile per il monitoraggio dello stato di un programma in fase di debug. A tale scopo, la Germania utilizza qualsiasi metodo è disponibili per il processo del runtime supportati, sia dalla CPU o dalle API fornita dal runtime.  
  
 Ad esempio, common language runtime (CLR) fornisce meccanismi per monitorare un programma in esecuzione tramite le interfacce ICorDebugXXX. Un CRI che supporta Common Language Runtime Usa le interfacce appropriate ICorDebugXXX per tenere traccia di un programma di codice gestito in fase di debug. Comunica quindi tutte le modifiche dello stato per la gestione di debug di sessione (SDM), che inoltra tali informazioni per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Un motore di debug destinato a una specifica del runtime, vale a dire, il sistema in cui il programma in fase di debug viene eseguito. CLR è il runtime per il codice gestito e il runtime di Win32 è per le applicazioni Windows native. Se la lingua è creare può avere come destinazione uno di questi due runtime, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce già i motori di debug necessari. Tutto ciò che devi implementare è un analizzatore di espressioni.  
  
## <a name="debug-engine-operation"></a>Operazione del motore di debug  
 I servizi di monitoraggio vengono implementati tramite le interfacce DE e possono causare il pacchetto di debug per la transizione tra diverse modalità operative. Per altre informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md). È in genere solo un'implementazione di DE per ogni ambiente run-time.  
  
> [!NOTE]
>  Anche se sono disponibili implementazioni separate di DE per Transact-SQL e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] condividono un singolo DE.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Abilita debug motori per eseguire una delle due modalità di debug: entrambi nello stesso processo come il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della shell o nello stesso processo come programma di destinazione in fase di debug. La seconda forma si verifica in genere quando il processo sottoposto a debug è effettivamente uno script in esecuzione con un interprete. Il motore di debug deve avere una conoscenza approfondita dell'interprete per monitorare lo script. In questo caso, l'interprete è effettivamente una fase di esecuzione. motori di debug sono per le implementazioni di specifica del runtime. Implementazione di un singolo DE, inoltre, può essere suddivise tra i limiti di processo e del computer (ad esempio, il debug remoto).  
  
 L'oggetto espone DE il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfacce di debug. Tutte le comunicazioni sono tramite COM. Se la Germania viene caricato in-process, out-of-process o in un altro computer, non influisce sulle comunicazioni di componente.  
  
 La Germania funziona con un componente dell'analizzatore di espressioni per abilitare il DE per quel particolare runtime comprendere la sintassi delle espressioni. La Germania funziona anche con un componente gestore di simboli per accedere alle informazioni di debug sui simboli generate dal compilatore del linguaggio. Per altre informazioni, vedere [analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) e [provider di simboli](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)