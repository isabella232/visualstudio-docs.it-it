---
title: Interfaccia IDebugSessionProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979048"
---
# <a name="idebugsessionprovider-interface"></a>Interfaccia IDebugSessionProvider
L'interfaccia primaria fornita da un IDE per consentire di host e la lingua di debug ha avviato il debug. Stabilisce una sessione di debug per un'applicazione in esecuzione. Questa interfaccia viene implementata per la gestione debug del computer.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugSessionProvider` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Avvia una sessione di debug con l'applicazione specificata.|