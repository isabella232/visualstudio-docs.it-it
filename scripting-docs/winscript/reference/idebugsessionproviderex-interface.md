---
title: Interfaccia IDebugSessionProviderEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae1cf673f47d3be586f83320b2d2c38c817e2cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349218"
---
# <a name="idebugsessionproviderex-interface"></a>Interfaccia IDebugSessionProviderEx
L'interfaccia primaria fornita da un debugger IDE per abilitare il debug avviato dall'host e linguaggio. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata per la gestione Debug del computer.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugSessionProviderEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina se il debug JIT è possibile eseguire con l'applicazione specificata.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|