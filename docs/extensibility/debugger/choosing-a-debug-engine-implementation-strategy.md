---
title: Scelta di una strategia di implementazione del motore di debug | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739122"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Scegliere una strategia di implementazione del motore di debug
Utilizzare l'architettura di run-time per determinare la strategia di implementazione del motore di debug. È possibile creare il motore di debug in-process per il programma di cui si esegue il debug. Creare il motore di debug in-process per Visual Studio Session Debug Manager (SDM). In alternativa, creare il motore di debug out-of-process in entrambi. Le linee guida seguenti consentono di scegliere tra queste tre strategie.

## <a name="guidelines"></a>Indicazioni
 Sebbene sia possibile che il DE sia out-of-process sia per SDM che per il programma di cui si sta eseguendo il debug, in genere non esiste alcun motivo. Le chiamate tra i limiti del processo sono relativamente lente.

 I motori di debug sono già disponibili per l'ambiente di runtime Win32 nativo e per l'ambiente Common Language Runtime. Se è necessario sostituire il valore DE per uno dei due ambienti, è necessario creare il DE in-process con SDM.

 In caso contrario, è possibile creare il DE in-process per SDM o in-process nel programma di cui si esegue il debug. È necessario considerare se l'analizzatore di espressioni di DE richiede l'accesso frequente all'archivio simboli del programma. In alternativa, se l'archivio simboli può essere caricato in memoria per l'accesso rapido. Considerare anche gli approcci seguenti:

- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio simboli oppure se l'archivio simboli può essere letto nello spazio di memoria SDM, creare il processo di Dein-Process per SDM. È necessario restituire il CLSID del motore di debug a SDM quando si connette al programma. SDM utilizza questo CLSID per creare un'istanza in-process del DE.

- Se il DE deve chiamare il programma per accedere all'archivio dei simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza del DE.

## <a name="see-also"></a>Vedere anche
- [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
