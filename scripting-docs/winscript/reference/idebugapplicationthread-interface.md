---
title: IDebugApplicationThread Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a464085eddbea4f5d29c684c0f1dabc6f853b6d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822226"
---
# <a name="idebugapplicationthread-interface"></a>Interfaccia IDebugApplicationThread
Consente di motori di linguaggio e gli host per fornire la sincronizzazione dei thread e per mantenere le informazioni sullo stato di debug specifico del thread. Questa interfaccia estende il `IRemoteDebugApplicationThread` interfaccia per fornire l'accesso non remoti per il thread.  
  
 Oltre ai metodi ereditati da `IRemoteDebugApplicationThread`, il `IDebugApplicationThread` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Fornisce un meccanismo per il chiamante può eseguire codice nel thread dell'applicazione.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina se il thread è il thread attualmente in esecuzione.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina se il thread è il thread del debugger.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Imposta la descrizione di questo thread.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Imposta la descrizione dello stato del thread.|