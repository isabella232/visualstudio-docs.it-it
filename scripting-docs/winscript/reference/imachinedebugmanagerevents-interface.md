---
title: Interfaccia IMachineDebugManagerEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153123"
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfaccia IMachineDebugManagerEvents
Segnala le modifiche all'elenco di applicazioni in esecuzione gestite dalla gestione del debug del computer. Questa interfaccia è utilizzabile per l'IDE di debug per visualizzare un elenco dinamico delle applicazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IMachineDebugManagerEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gestisce l'evento quando un'applicazione viene aggiunto all'esecuzione elenco delle applicazioni.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gestisce l'evento quando un'applicazione viene rimossa l'esecuzione di elenco di applicazioni.|