---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f47877b5bea1a65961ae7be6d7018e18fb03cd8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748426"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia di notifica a un listener (in genere la sessione gestione debug [SDM] o un motore di debug) del processo e il programma di creazione e l'eliminazione su una porta specifica. Queste informazioni sono utilizzabile per presentare una visualizzazione in tempo reale dei processi e i programmi in esecuzione sulla porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa in genere questa interfaccia per ricevere notifiche sulla creazione di un programma e l'eliminazione. Un motore di debug è anche possibile implementare questa interfaccia per l'ascolto degli eventi di questo tipo porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Tutti i [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfacce è possibile eseguire query per un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodo per `IDebugPortEvents2` viene chiamato <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia da ottenere un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia. Infine, il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo nella <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene chiamata per inviare gli eventi tramite il [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) (metodo).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente illustra il metodo di `IDebugPortEvents2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia gli eventi che descrivono la creazione e l'eliminazione dei processi e dei programmi sulla porta.|  
  
## <a name="remarks"></a>Note  
 `IDebugPortEvents2` viene usato anche per il modello SDM per eseguire il debug di programmi in esecuzione in un processo già in fase di debug.  
  
 Gli eventi porta vengono passati per il modello SDM per questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

