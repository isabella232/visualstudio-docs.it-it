---
title: Implementazione di un fornitore di porte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152684"
---
# <a name="implementing-a-port-supplier"></a>Implementazione di un fornitore di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fornitore di porte fornisce porte su richiesta a gestione debug sessione (SDM). Un fornitore di porte deve essere implementato durante il debug in un computer non DCOM o quando è necessario supportare un nuovo dispositivo. Ad esempio, per fornire il debug a un telefono cellulare, è possibile implementare un fornitore di porte che fornisce le porte che si connettono al telefono cellulare (probabilmente per mezzo di IR o una connessione di cella) ed enumera i processi e i programmi in esecuzione sul telefono.  
  
 Per il debug di programmi in computer basati su Windows (incluso il debug remoto), Visual Studio fornisce i fornitori di porte per i processi nativi e Common Language Runtime (CLR), quindi non è necessario implementare il proprio fornitore di porte in questi casi.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementazione e registrazione di un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Viene illustrato il modo in cui SDM interagisce con il fornitore della porta e le relative porte.  
  
 [Interfacce obbligatorie dei fornitori di porte](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta le interfacce che devono essere implementate per ottenere un fornitore di porte.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
