---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d062fe93a18b88cd6c24e0ece18d30f186c6420f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777032"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente a un motore di debug eseguire l'override del comportamento predefinito del [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente quando si termina una sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dai motori di debug. È utile per gli host che potrebbero creare ed eliminare più programmi in base alla durata di un processo.  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramDestroyEventFlags2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera il programma di eliminare definitivamente i flag.|  
  
## <a name="remarks"></a>Note  
 Il comportamento predefinito del [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente consiste nel tornare alla modalità progettazione dopo che tutti i programmi sono inviate a un programma un evento di eliminazione. Questa interfaccia consente a un motore di debug modificare tale comportamento.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

