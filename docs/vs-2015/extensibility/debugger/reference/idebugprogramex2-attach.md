---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1969f8d38cd52572f0d0c7cde603a1ea25c0e0be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527630"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProgramEx2::Attach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramex2-attach).  
  
Connettere una sessione a un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Un' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto che rappresenta la funzione di callback che il motore di debug collegati invia eventi.  
  
 `dwReason`  
 [in] Un valore compreso il [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che descrive il motivo per l'operazione di collegamento.  
  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione che si sta connettendo al programma.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già collegato.  
  
## <a name="remarks"></a>Note  
 La porta che contiene il programma può usare il valore in `pSession` per determinare quale sessione sta tentando di collegare al programma. Ad esempio, se una porta consente di sessione di debug solo una per connettersi a un processo alla volta, la porta possibile determinare se la stessa sessione è già collegata ad altri programmi nel processo.  
  
> [!NOTE]
>  L'interfaccia passato `pSession` deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug sessione la connessione a questo programma; nessuno dei metodi nell'interfaccia specificata sono funzionali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
