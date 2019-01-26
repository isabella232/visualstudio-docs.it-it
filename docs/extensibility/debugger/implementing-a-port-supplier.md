---
title: Implementazione di un fornitore di porte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e59ad83499e69bcf257ae212c18b14fba208f3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025813"
---
# <a name="implement-a-port-supplier"></a>Implementare un fornitore di porte
Un fornitore di porte fornisce porte di richiesta al gestore di sessione di debug (SDM). Durante il debug in un computer non DCOM o quando un nuovo dispositivo richiede il supporto è necessario implementare un fornitore di porte. Ad esempio, per offrire debug in un telefono cellulare, è possibile impostare backup di un fornitore di porte che fornisce le porte, connettersi al telefono cellulare (magari tramite una connessione di cella o di runtime di integrazione), che enumera i processi e i programmi in esecuzione sul telefono.  
  
 Debug dei programmi nei computer basati su Windows (incluso il debug remoto), Visual Studio offre fornitori di porte per i processi di Common Language Runtime (CLR) e native in modo che non è necessario configurare il proprio fornitore di porte in questi casi.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementare e registrare un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Viene descritto come il modello SDM interagisce con il fornitore della porta e le relative porte.  
  
 [Porta richiesta supplier interfacce](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Vengono documentate le interfacce che devono implementare per ottenere un fornitore di porte.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Descrive i principali concetti dell'architettura di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)