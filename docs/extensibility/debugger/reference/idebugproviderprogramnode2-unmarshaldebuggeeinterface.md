---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af69580293e4ff37d0a23e3050955c96cc8f10b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988272"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Ottiene un'interfaccia specificata nell'ambito dei processi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `riid`  
 [in] GUID dell'interfaccia da ottenere.  
  
 `ppvObject`  
 [out] Restituisce l'oggetto che implementa l'interfaccia desiderata. [C++] e può essere eseguito il cast direttamente al tipo di interfaccia desiderata. [C#] usare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodo per ottenere l'interfaccia desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato quando il motore di debug è in esecuzione il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] spazio del processo e il programma sottoposto a debug è in esecuzione nel proprio spazio di processo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)