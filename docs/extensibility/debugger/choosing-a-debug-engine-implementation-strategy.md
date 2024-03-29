---
title: Scelta di una strategia di implementazione del motore di debug | Microsoft Docs
description: Informazioni su come l'architettura di runtime consente di scegliere tra diverse strategie per l'implementazione del motore di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 22077acd9e669f82d274a11a2b983c01afd1f746
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709805"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Scegliere una strategia di implementazione del motore di debug
Usare l'architettura di runtime per determinare la strategia di implementazione del motore di debug. È possibile creare il motore di debug in-process per il programma di cui si esegue il debug. Creare il motore di debug in-process per la Visual Studio di debug della sessione di debug (SDM). In caso contrario, creare il motore di debug out-of-process per entrambi. Le linee guida seguenti consentono di scegliere tra queste tre strategie.

## <a name="guidelines"></a>Indicazioni
 Anche se è possibile che DE sia out-of-process sia per SDM che per il programma di cui si esegue il debug, in genere non c'è alcun motivo per farlo. Le chiamate attraverso i limiti dei processi sono relativamente lente.

 I motori di debug sono già disponibili per l'ambiente di runtime nativo Win32 e per l'ambiente di runtime common language. Se è necessario sostituire de per entrambi gli ambienti, è necessario creare de-process con SDM.

 In caso contrario, è possibile creare de-process in SDM o in-process per il programma di cui si esegue il debug. È necessario considerare se l'analizzatore di espressioni di DE richiede l'accesso frequente all'archivio dei simboli del programma. Oppure, se l'archivio dei simboli può essere caricato in memoria per un accesso rapido. Considerare anche gli approcci seguenti:

- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio dei simboli o se l'archivio dei simboli può essere letto nello spazio di memoria SDM, creare de-process in SDM. È necessario restituire il CLSID del motore di debug a SDM quando si collega al programma. SDM usa questo CLSID per creare un'istanza in-process del de.

- Se DE deve chiamare il programma per accedere all'archivio dei simboli, creare de-process con il programma. In questo caso, il programma crea l'istanza del de.

## <a name="see-also"></a>Vedi anche
- [Visual Studio estensibilità del debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
