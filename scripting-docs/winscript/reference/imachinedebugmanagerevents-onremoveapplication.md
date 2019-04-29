---
title: IMachineDebugManagerEvents::onRemoveApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onRemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onRemoveApplication
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87ae129448de4425f961038739cfc05c87e285e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965323"
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Gestisce l'evento quando un'applicazione viene rimossa l'esecuzione di elenco di applicazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 [in] Applicazione che è stato rimosso dall'esecuzione elenco delle applicazioni.  
  
 `dwAppCookie`  
 [in] Il cookie specificato quando l'applicazione è stata aggiunta dall'elenco di applicazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo indica che un'applicazione è stata rimossa l'esecuzione di elenco di applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)