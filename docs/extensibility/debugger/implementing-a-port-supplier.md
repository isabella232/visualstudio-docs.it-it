---
title: Implementazione di un fornitore di porte | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738551"
---
# <a name="implement-a-port-supplier"></a>Implementare un fornitore di porte
Un fornitore di porte fornisce porte su richiesta a gestione debug sessione (SDM). Un fornitore di porte deve essere implementato durante il debug in un computer non DCOM o quando un nuovo dispositivo richiede il supporto. Ad esempio, per fornire il debug a un telefono cellulare, è possibile configurare un fornitore di porte che fornisce le porte, che si connettono al telefono cellulare (probabilmente tramite IR o una connessione di cella) ed enumera i processi e i programmi in esecuzione sul telefono.

 Per il debug di programmi in computer basati su Windows (incluso il debug remoto), Visual Studio fornisce i fornitori di porte per i processi nativi e Common Language Runtime (CLR), quindi non è necessario configurare il proprio fornitore di porte in questi casi.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare e registrare un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Viene illustrato il modo in cui SDM interagisce con il fornitore della porta e le relative porte.

 [Interfacce del fornitore di porte obbligatorie](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta le interfacce che è necessario implementare per ottenere un fornitore di porte.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i principali concetti dell'architettura di debug.

## <a name="see-also"></a>Vedere anche
 [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
