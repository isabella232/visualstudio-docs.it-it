---
title: Scelta di una strategia di implementazione del motore di debug | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183462"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Scelta di una strategia di implementazione del motore di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilizzare l'architettura di run-time per determinare la strategia di implementazione del motore di debug. Il motore di debug può essere creato in-process per il programma di cui eseguire il debug, in-process per Visual Studio Session Debug Manager (SDM) o out-of-process. Le linee guida seguenti consentono di scegliere tra queste tre strategie.  
  
## <a name="guidelines"></a>Indicazioni  
 Sebbene sia possibile che il DE sia out-of-process sia per SDM che per il programma di cui eseguire il debug, non esiste in genere alcun motivo. Le chiamate tra i limiti del processo sono relativamente lente.  
  
 I motori di debug sono già disponibili per l'ambiente di runtime Win32 nativo e per l'ambiente Common Language Runtime. Se è necessario sostituire il DE per uno di questi ambienti, è necessario creare il DE in-process con SDM.  
  
 In caso contrario, è possibile scegliere di creare il DE in-process per SDM o in-process per il programma di cui eseguire il debug. È importante valutare se l'analizzatore di espressioni di DE richiede l'accesso frequente all'archivio dei simboli del programma e se l'archivio simboli può essere caricato in memoria per l'accesso rapido. Tenere inoltre in considerazione quanto segue:  
  
- Se non sono presenti molte chiamate tra l'analizzatore di espressioni e l'archivio simboli oppure se l'archivio simboli può essere letto nello spazio di memoria SDM, creare il processo di Dein-Process per SDM. È necessario restituire il CLSID del motore di debug a SDM quando si connette al programma. SDM utilizza questo CLSID per creare un'istanza in-process del DE.  
  
- Se il DE deve chiamare il programma per accedere all'archivio dei simboli, creare il DE in-process con il programma. In questo caso, il programma crea l'istanza del DE.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
