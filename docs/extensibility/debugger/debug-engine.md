---
title: Motore di debug - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739061"
---
# <a name="debug-engine"></a>Motore di debug
Un motore di debug (DE) funziona con l'interprete o il sistema operativo per fornire servizi di debug come il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni. Il DE è responsabile del monitoraggio dello stato di un programma in fase di debug. A tale scopo, il DE utilizza tutti i metodi disponibili nel runtime supportato, sia dalla CPU o dalle API fornite dal runtime.

 Ad esempio, Common Language Runtime (CLR) fornisce meccanismi per monitorare un programma in esecuzione tramite il ICorDebugXXX interfacce. Un DE che supporta CLR utilizza le interfacce ICorDebugXXX appropriate per tenere traccia di un programma di codice gestito in fase di debug. Comunica quindi tutte le modifiche di stato al gestore di sessione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug (SDM), che inoltra tali informazioni all'IDE.

> [!NOTE]
> Un motore di debug è destinato a un runtime specifico, ovvero il sistema in cui viene eseguito il programma sottoposto a debug. CLR è il runtime per il codice gestito e il runtime Win32 è per le applicazioni Windows native. Se il linguaggio creato può essere destinato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a uno di questi due runtime, fornisce già i motori di debug necessari. Tutto quello che devi implementare è un analizzatore di espressioni.

## <a name="debug-engine-operation"></a>Funzionamento del motore di debugDebug engine operation
 I servizi di monitoraggio vengono implementati tramite le interfacce DE e possono causare la transizione del pacchetto di debug tra diverse modalità operative. Per ulteriori informazioni, consultate [Modalità operative.](../../extensibility/debugger/operational-modes.md) In genere esiste una sola implementazione DE per ogni ambiente di runtime.

> [!NOTE]
> Sebbene esistano implementazioni DE [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]separate per [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] Transact-SQLTransact-SQL e , VBScript e condividere un singolo DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug consente ai motori di debug di eseguire [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in uno dei due modi seguenti: nello stesso processo della shell o nello stesso processo del programma di destinazione in fase di debug. Quest'ultimo formato si verifica in genere quando il processo sottoposto a debug è in realtà uno script in esecuzione con un interprete. Il motore di debug deve avere una conoscenza approfondita dell'interprete per monitorare lo script. In questo caso, l'interprete è in realtà un runtime; I motori di debug sono per implementazioni di runtime specifiche. Inoltre, l'implementazione di un singolo DE può essere suddivisa tra i limiti del processo e del computer (ad esempio, il debug remoto).

 Il DE espone [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le interfacce di debug. Tutte le comunicazioni avvengono tramite COM. Se il DE viene caricato in-process, out-of-process o in un altro computer, non influisce sulla comunicazione del componente.

 Il DE funziona con un componente dell'analizzatore di espressioni per consentire al DE per quel particolare runtime di comprendere la sintassi delle espressioni. Il DE funziona anche con un componente gestore di simboli per accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio. Per ulteriori informazioni, consultate [Analizzatore di](../../extensibility/debugger/expression-evaluator.md) espressioni e [Provider di simboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Valutatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
