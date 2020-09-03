---
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202825"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo aggiunge un nodo di programma per ogni motore di debug (DE) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidLaunchingEngine`  
 in `GUID` Di un de da usare per avviare i programmi (si presuppone che aggiunga i propri nodi del programma).  
  
 `rgguidSpecificEngines`  
 in Matrice di `GUID` des per cui verranno aggiunti i nodi del programma.  
  
 `celtSpecificEngines`  
 in Numero di `GUID` s nella `rgguidSpecificEngines` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 I [nodi del programma](../../../extensibility/debugger/program-nodes.md) verranno aggiunti per ogni de elencato in, `rgguidSpecificEngines` escluso il motore di avvio (come indicato in `guidLaunchingEngine` ), che si presuppone aggiungere il proprio nodo di programma all'avvio di un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nodi di programma](../../../extensibility/debugger/program-nodes.md)
