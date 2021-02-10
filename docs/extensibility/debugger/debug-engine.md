---
title: Motore di debug | Microsoft Docs
description: Informazioni sul funzionamento di un motore di debug con l'interprete o il sistema operativo per fornire servizi quali il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e278b83e69a063c88b4cb3ff48d919d2b07ea6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955164"
---
# <a name="debug-engine"></a>Motore di debug
Un motore di debug (DE) funziona con l'interprete o il sistema operativo per fornire servizi di debug, ad esempio il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni. Il DE è responsabile del monitoraggio dello stato di un programma di cui è in corso il debug. A tale scopo, il DE usa qualsiasi metodo disponibile nel runtime supportato, sia dalla CPU che dalle API fornite dal runtime.

 Il Common Language Runtime (CLR), ad esempio, fornisce meccanismi per il monitoraggio di un programma in esecuzione tramite le interfacce ICorDebugXXX. Un DE che supporta CLR usa le interfacce ICorDebugXXX appropriate per tenere traccia di un programma di codice gestito di cui è in corso il debug. Comunica quindi qualsiasi modifica dello stato al gestore di debug della sessione (SDM), che li trasmette all' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

> [!NOTE]
> Un motore di debug è destinato a un runtime specifico, ovvero al sistema in cui viene eseguito il programma di cui è in corso il debug. CLR è il runtime per il codice gestito e il runtime Win32 è per le applicazioni Windows native. Se la lingua creata può essere destinata a uno di questi due runtime, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce già i motori di debug necessari. È necessario implementare solo un analizzatore di espressioni.

## <a name="debug-engine-operation"></a>Operazione del motore di debug
 I servizi di monitoraggio vengono implementati tramite le interfacce DE e possono causare la transizione del pacchetto di debug tra diverse modalità operative. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md). In genere esiste solo un'implementazione di DE per ogni ambiente di run-time.

> [!NOTE]
> Anche se sono presenti implementazioni di DE separate per Transact-SQL e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] condividono un solo de.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug consente ai motori di debug di eseguire uno dei due modi seguenti: nello stesso processo della [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell o nello stesso processo del programma di destinazione di cui è in corso il debug. Il secondo formato si verifica in genere quando il processo di cui è in corso il debug è in realtà uno script in esecuzione in un interprete. Il motore di debug deve avere una conoscenza approfondita dell'interprete per eseguire il monitoraggio dello script. In questo caso, l'interprete è in realtà un Runtime; i motori di debug sono per implementazioni specifiche del runtime. Inoltre, l'implementazione di un singolo DE può essere suddivisa tra i limiti del processo e del computer, ad esempio il debug remoto.

 Il DE espone le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfacce di debug. Tutte le comunicazioni vengono comunicate tramite COM. Se il valore DE viene caricato in-process, out-of-process o in un altro computer, non influisce sulla comunicazione dei componenti.

 Il valore DE è compatibile con un componente dell'analizzatore di espressioni per consentire al DE per quel particolare runtime di comprendere la sintassi delle espressioni. Il DE funziona anche con un componente del gestore di simboli per accedere alle informazioni di debug simboliche generate dal compilatore di linguaggio. Per ulteriori informazioni, vedere l' [analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md) e il [provider di simboli](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Provider di simboli](../../extensibility/debugger/symbol-provider.md)
