---
title: Motore di debug | Microsoft Docs
description: Informazioni sul funzionamento di un motore di debug con l'interprete o il sistema operativo per fornire servizi come il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4836141f50f2db13ad0fd303168d291b56ab1643
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111749"
---
# <a name="debug-engine"></a>Motore di debug
Un motore di debug (DE) funziona con l'interprete o il sistema operativo per fornire servizi di debug, ad esempio controllo dell'esecuzione, punti di interruzione e valutazione delle espressioni. Il de è responsabile del monitoraggio dello stato di un programma in fase di debug. A tale scopo, il DE usa tutti i metodi disponibili nel runtime supportato, sia dalla CPU che dalle API fornite dal runtime.

 Ad esempio, Common Language Runtime (CLR) fornisce meccanismi per monitorare un programma in esecuzione tramite le interfacce ICorDebugXXX. Un de che supporta CLR usa le interfacce ICorDebugXXX appropriate per tenere traccia del debug di un programma di codice gestito. Comunica quindi eventuali modifiche di stato al gestore di debug sessione (SDM), che inoltra tali informazioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] all'IDE.

> [!NOTE]
> Un motore di debug è destinato a un runtime specifico, ovvero il sistema in cui viene eseguito il programma di cui viene eseguito il debug. CLR è il runtime per il codice gestito e il runtime Win32 è per le applicazioni Windows native. Se il linguaggio creato può essere utilizzato come destinazione di uno di questi due runtime, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce già i motori di debug necessari. È necessario implementare solo un analizzatore di espressioni.

## <a name="debug-engine-operation"></a>Eseguire il debug dell'operazione del motore
 I servizi di monitoraggio vengono implementati tramite le interfacce DE e possono causare la transizione del pacchetto di debug tra modalità operative diverse. Per altre informazioni, vedere [Modalità operative](../../extensibility/debugger/operational-modes.md). In genere è presente una sola implementazione di DE per ogni ambiente di run-time.

> [!NOTE]
> Sebbene siano disponibili implementazioni DE separate per Transact-SQL [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] e , VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] condividono un singolo DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug consente ai motori di debug di eseguire uno dei due modi seguenti: nello stesso processo della shell o nello stesso processo del programma di destinazione di cui viene eseguito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug. Quest'ultima forma si verifica in genere quando il processo di cui viene eseguito il debug è in realtà uno script in esecuzione in un interprete. Il motore di debug deve avere una conoscenza approfondita dell'interprete per monitorare lo script. In questo caso, l'interprete è effettivamente un runtime. I motori di debug sono per implementazioni di runtime specifiche. Inoltre, l'implementazione di un singolo DE può essere suddivisa tra i limiti del processo e del computer (ad esempio, il debug remoto).

 Il de espone le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfacce di debug. Tutte le comunicazioni sono tramite COM. Se il de viene caricato in-process, out-of-process o in un altro computer, non influisce sulla comunicazione dei componenti.

 De funziona con un componente dell'analizzatore di espressioni per consentire al de per quel particolare runtime di comprendere la sintassi delle espressioni. Il de funziona anche con un componente gestore simboli per accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio. Per altre informazioni, vedere [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) e [Provider di simboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
