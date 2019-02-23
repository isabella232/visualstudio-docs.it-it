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
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685924"
---
# <a name="implement-a-port-supplier"></a>Implementare un fornitore di porte
Un fornitore di porte fornisce porte di richiesta al gestore di sessione di debug (SDM). Durante il debug in un computer non DCOM o quando un nuovo dispositivo richiede il supporto è necessario implementare un fornitore di porte. Ad esempio, per offrire debug in un telefono cellulare, è possibile impostare backup di un fornitore di porte che fornisce le porte, connettersi al telefono cellulare (magari tramite una connessione di cella o di runtime di integrazione), che enumera i processi e i programmi in esecuzione sul telefono.

 Debug dei programmi nei computer basati su Windows (incluso il debug remoto), Visual Studio offre fornitori di porte per i processi di Common Language Runtime (CLR) e native in modo che non è necessario configurare il proprio fornitore di porte in questi casi.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare e registrare un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) viene illustrato come il modello SDM interagisce con il fornitore della porta e le relative porte.

 [Interfacce di fornitori di porte necessarie](../../extensibility/debugger/required-port-supplier-interfaces.md) documenta le interfacce devono implementare per ottenere un fornitore di porte.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) vengono descritti i principali concetti dell'architettura di debug.

## <a name="see-also"></a>Vedere anche
 [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)