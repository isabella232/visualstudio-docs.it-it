---
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b60801f5288e88795ab75145b9c6120d4308d1c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202990"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un oggetto che usa un costruttore, date le impostazioni dei flag di valutazione e un valore di timeout.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pConstructor`  
 in Oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) che rappresenta il costruttore dell'oggetto da creare.  
  
 `dwArgs`  
 in Numero di parametri nella `pArg` matrice. Rappresenta il numero di parametri passati al costruttore.  
  
 `pArgs`  
 in Matrice di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri passati al costruttore.  
  
 `dwEvalFlags`  
 in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.  
  
 `dwTimeout`  
 in Tempo massimo, in millisecondi, di attesa prima che venga restituito da questo metodo. Usare **infinito** per un'attesa indefinita.  
  
 `ppObject`  
 out Restituisce un **IDebugObject** che rappresenta l'oggetto appena creato.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe o un altro tipo complesso che richiede un costruttore, ovvero un parametro.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
