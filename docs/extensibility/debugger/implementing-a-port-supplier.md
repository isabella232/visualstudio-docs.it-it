---
title: Implementazione di un fornitore di porte Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738551"
---
# <a name="implement-a-port-supplier"></a>Implementare un fornitore di porte
Un fornitore di porte fornisce le porte su richiesta al gestore di sessione di debug (SDM). Un fornitore di porte deve essere implementato durante il debug su un computer non DCOM o quando un nuovo dispositivo richiede supporto. Ad esempio, per fornire il debug a un telefono cellulare, è possibile impostare un fornitore di porte che fornisce le porte, che si connettono al telefono cellulare (ad esempio tramite IR o una connessione cellulare) ed enumera i processi e i programmi in esecuzione sul telefono.

 Per il debug di programmi su computer basati su Windows (incluso il debug remoto), Visual Studio fornisce fornitori di porte per i processi nativi e CLR (Common Language Runtime), pertanto non è necessario configurare il proprio fornitore di porta in questi casi.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare e registrare un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Viene illustrato come il file SDM interagisce con il fornitore della porta e le relative porte.

 [Interfacce fornitore porta richieste](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta le interfacce che è necessario implementare per ottenere un fornitore di porta.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali relativi all'architettura di debug.

## <a name="see-also"></a>Vedere anche
 [Estendibilità del debugger di Visual StudioVisual Studio debugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
