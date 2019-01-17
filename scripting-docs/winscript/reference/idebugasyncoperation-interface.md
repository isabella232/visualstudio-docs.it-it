---
title: Interfaccia IDebugAsyncOperation | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0088fddd2661d6711c9a18495f4b8704f782b3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349991"
---
# <a name="idebugasyncoperation-interface"></a>Interfaccia IDebugAsyncOperation
Implementa il gestore di eseguire il Debug di processi di `IDebugAsyncOperation` interfaccia. Un motore del linguaggio chiama il `IDebugApplication::CreateAsyncDebugOperation` metodo per ottenere un riferimento a questa interfaccia. Il motore di linguaggio può usare il `IDebugAsyncOperation` interfaccia per fornire l'accesso asincrono a un'operazione di debug sincrono.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugAsyncOperation` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Restituisce l'operazione di debug sincrono associato all'oggetto.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Fa sì che l'operazione asincrona iniziare.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Annulla un'operazione.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Determina se l'operazione di debug è stata completata.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Fornisce il valore restituito e parametro dell'oggetto restituito dall'operazione di debug sincrono.|