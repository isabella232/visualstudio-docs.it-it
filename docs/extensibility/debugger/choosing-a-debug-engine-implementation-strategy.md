---
title: Scelta di una strategia di implementazione del motore di debug Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739122"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Scegliere una strategia di implementazione del motore di debugChoose a debug engine implementation strategy
Utilizzare l'architettura di runtime per determinare la strategia di implementazione del motore di debug (DE). È possibile creare il motore di debug in-process per il programma che si sta eseguendo il debug. Creare il motore di debug in-process per il gestore di debug sessione di Visual Studio (SDM). In alternativa, creare il motore di debug out-of-process per entrambi. Le seguenti linee guida dovrebbero aiutarti a scegliere tra queste tre strategie.

## <a name="guidelines"></a>Indicazioni
 Mentre è possibile che il DE sia out-of-process sia per il Modello SDM che per il programma di cui si sta eseguendo il debug, in genere non c'è motivo di farlo. Le chiamate oltre i limiti del processo sono relativamente lente.

 I motori di debug sono già disponibili per l'ambiente di runtime nativo Win32 e per l'ambiente di runtime del linguaggio comune. Se è necessario sostituire il DE per entrambi gli ambienti, è necessario creare il DE in-process con il modello SDM.

 In caso contrario, si crea il DE in-process per il modello SDM o in-process per il programma di cui si sta eseguendo il debug. È necessario considerare se l'analizzatore di espressioni del DE richiede l'accesso frequente all'archivio di simboli di programma. In alternativa, se l'archivio simboli può essere caricato in memoria per un accesso rapido. Considerare inoltre i seguenti approcci:

- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio simboli o se l'archivio simboli può essere letto nello spazio di memoria SDM, creare il DE in-process per il modello SDM. È necessario restituire il CLSID del motore di debug al sistema SDM quando si connette al programma. Il modello SDM utilizza questo CLSID per creare un'istanza in-process del DE.

- Se il DE deve chiamare il programma per accedere all'archivio di simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza del DE.

## <a name="see-also"></a>Vedere anche
- [Estendibilità del debugger di Visual StudioVisual Studio debugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
