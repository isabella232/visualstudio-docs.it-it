---
title: Interfaccia IMachineDebugManagerEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344030"
---
# <a name="imachinedebugmanagerevents-interface"></a>Interfaccia IMachineDebugManagerEvents
Segnala le modifiche all'elenco di applicazioni in esecuzione gestite dalla gestione del debug del computer. Questa interfaccia è utilizzabile per l'IDE di debug per visualizzare un elenco dinamico delle applicazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IMachineDebugManagerEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Gestisce l'evento quando un'applicazione viene aggiunto all'esecuzione elenco delle applicazioni.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Gestisce l'evento quando un'applicazione viene rimossa l'esecuzione di elenco di applicazioni.|