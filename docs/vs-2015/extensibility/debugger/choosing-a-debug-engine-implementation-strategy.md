---
title: Scelta di una strategia di implementazione del motore di Debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183462"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Scelta di una strategia di implementazione del motore di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilizzare l'architettura di runtime per determinare la strategia di implementazione (DE) del motore di debug. Il motore di debug può essere creato in-process per il programma da sottoporre a debug, in-process per la gestione di debug di Visual Studio sessioni (SDM) o out-of-process per entrambi i sistemi operativi. Le linee guida seguenti consentono di scegliere tra queste tre strategie.  
  
## <a name="guidelines"></a>Indicazioni  
 Sebbene sia possibile per la Germania sia out-of-process per il modello SDM sia il programma da sottoporre a debug, non è in genere necessario eseguire questa operazione. Le chiamate tra i limiti dei processi sono relativamente lente.  
  
 Eseguire il debug motori sono già forniti per l'ambiente di runtime Win32 native e per l'ambiente di common language runtime. Se è necessario sostituire il DE per uno di questi ambienti, è necessario creare il DE in-process con il modello SDM.  
  
 In caso contrario, è possibile scegliere tra la creazione di DE in-process per il modello SDM o in-process per il programma da sottoporre a debug. È importante considerare se l'analizzatore di espressioni della DE accede di frequente per l'archivio dei simboli programma e indica se l'archivio dei simboli può essere caricata in memoria per l'accesso rapido. Considerare anche quanto segue:  
  
- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio dei simboli, o se l'archivio dei simboli può essere letti in spazio di memoria SDM, creare il DE per il modello SDM in-process. È necessario restituire il CLSID del motore di debug per il modello SDM al momento del collegamento al programma. Il modello SDM Usa questo CLSID per creare un'istanza in-process della DE.  
  
- Se la Germania deve chiamare il programma per accedere all'archivio di simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza della DE.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
