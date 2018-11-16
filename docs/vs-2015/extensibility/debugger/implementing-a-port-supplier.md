---
title: Implementazione di un fornitore di porte | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0596809ceccd3d528e3276f2ed310a4835c836eb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738766"
---
# <a name="implementing-a-port-supplier"></a>Implementazione di un fornitore di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fornitore di porte fornisce porte di richiesta al gestore di sessione di debug (SDM). Un fornitore di porte deve essere implementata durante il debug in un computer non DCOM o quando un nuovo dispositivo deve essere supportato. Ad esempio, per offrire debug in un telefono cellulare, è possibile implementare un fornitore di porte che fornisce porte che si connettono al telefono cellulare (magari tramite una connessione di cella o di runtime di integrazione) ed enumera i processi e i programmi in esecuzione sul telefono.  
  
 Debug dei programmi nei computer basati su Windows (incluso il debug remoto), Visual Studio offre fornitori di porte per i processi di Common Language Runtime (CLR) e native in modo che non è necessario implementare il proprio fornitore di porte in questi casi.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione e registrazione di un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Viene descritto come il modello SDM interagisce con il fornitore della porta e le relative porte.  
  
 [Interfacce obbligatorie dei fornitori di porte](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Vengono documentate le interfacce che devono essere implementate per ottenere un fornitore di porte.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

