---
title: Interfaccia IDispError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345838"
---
# <a name="idisperror-interface"></a>Interfaccia IDispError
Fornisce informazioni contestuali dettagliate.  
  
> [!NOTE]
>  Questa interfaccia non è implementata.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDispError` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Recupera un determinato tipo di informazioni sull'errore.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Recupera il successivo `IDispError` oggetto.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Recupera il codice di errore di `IDispError` oggetto.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Restituisce l'identificatore a livello di codice dipendente dalla lingua per la classe o un'applicazione che ha generato l'errore.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Restituisce il percorso del file della Guida e l'ID del contesto dell'argomento che spiega l'errore, se possibile.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Restituisce una descrizione testuale dell'errore.|