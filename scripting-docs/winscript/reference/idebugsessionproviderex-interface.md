---
title: Interfaccia IDebugSessionProviderEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978996"
---
# <a name="idebugsessionproviderex-interface"></a>Interfaccia IDebugSessionProviderEx
L'interfaccia primaria fornita da un debugger IDE per abilitare il debug avviato dall'host e linguaggio. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata per la gestione Debug del computer.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugSessionProviderEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina se il debug JIT è possibile eseguire con l'applicazione specificata.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|