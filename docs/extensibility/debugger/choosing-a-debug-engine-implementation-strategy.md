---
title: Scelta di una strategia di implementazione del motore di Debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 245fb14b06b5deed5ee652ef394e241bd1191022
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890684"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Scegliere una strategia di implementazione del motore di debug
Utilizzare l'architettura di runtime per determinare la strategia di implementazione (DE) del motore di debug. È possibile creare il debug del motore in-process per il programma di che debug. Creare il debug del motore in-process per la gestione di debug di Visual Studio sessione (SDM). In alternativa, creare il debug del motore out-of-process per entrambi i sistemi operativi. Le linee guida seguenti consentono di scegliere tra queste tre strategie.

## <a name="guidelines"></a>Indicazioni
 Sebbene sia possibile per la Germania sia out-of-process per il modello SDM e il programma si esegue il debug, non è in genere necessario eseguire questa operazione. Le chiamate tra i limiti dei processi sono relativamente lente.

 Eseguire il debug motori sono già forniti per l'ambiente di runtime Win32 native e per l'ambiente di common language runtime. Se è necessario sostituire il DE per entrambi gli ambienti, è necessario creare il DE in-process con il modello SDM.

 In caso contrario, si crea il DE per il modello SDM in-process o in-process per il programma di debug. È necessario prendere in considerazione se l'analizzatore di espressioni della DE richiede l'accesso frequente per l'archivio dei simboli programma. In alternativa, se l'archivio dei simboli può essere caricata in memoria per l'accesso rapido. Inoltre, prendere in considerazione gli approcci seguenti:

- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio dei simboli, o se l'archivio dei simboli può essere letti in spazio di memoria SDM, creare il DE per il modello SDM in-process. È necessario restituire il CLSID del motore di debug per il modello SDM al momento del collegamento al programma. Il modello SDM Usa questo CLSID per creare un'istanza in-process della DE.

- Se la Germania deve chiamare il programma per accedere all'archivio di simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza della DE.

## <a name="see-also"></a>Vedere anche
- [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)