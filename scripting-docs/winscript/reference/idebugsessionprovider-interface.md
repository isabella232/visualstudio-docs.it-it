---
title: Interfaccia IDebugSessionProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345149"
---
# <a name="idebugsessionprovider-interface"></a>Interfaccia IDebugSessionProvider
L'interfaccia primaria fornita da un IDE per consentire di host e la lingua di debug ha avviato il debug. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata per la gestione debug del computer.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugSessionProvider` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|