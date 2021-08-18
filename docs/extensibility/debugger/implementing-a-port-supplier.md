---
title: Implementazione di un fornitore di porte | Microsoft Docs
description: Informazioni sull'implementazione di un fornitore di porte, che è necessario quando si esegue il debug in un computer non DCOM o quando un nuovo dispositivo richiede il supporto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 383579e3d34213e4e5d5a4db6b4eeb8e554cb796
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043531"
---
# <a name="implement-a-port-supplier"></a>Implementare un fornitore di porte
Un fornitore di porte fornisce le porte su richiesta al gestore di debug sessione (SDM). Un fornitore di porte deve essere implementato durante il debug in un computer non DCOM o quando un nuovo dispositivo richiede il supporto. Ad esempio, per fornire il debug a un telefono cellulare, è possibile configurare un fornitore di porte che fornisce le porte, che si connettono al telefono cellulare (ad esempio tramite IR o una connessione cellulare) ed enumera i processi e i programmi in esecuzione sul telefono.

 Per il debug di programmi in computer basati su Windows (incluso il debug remoto), Visual Studio fornisce fornitori di porte per i processi nativi e CLR (Common Language Runtime), quindi non è necessario configurare il proprio fornitore di porte in questi casi.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementare e registrare un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Viene illustrato il modo in cui SDM interagisce con il fornitore della porta e le relative porte.

 [Interfacce del fornitore di porte necessarie](../../extensibility/debugger/required-port-supplier-interfaces.md) Documenta le interfacce che è necessario implementare per ottenere un fornitore di porte.

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali dell'architettura di debug.

## <a name="see-also"></a>Vedi anche
 [Visual Studio estendibilità del debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
