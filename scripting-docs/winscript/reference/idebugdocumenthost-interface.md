---
title: Interfaccia IDebugDocumentHost | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46684bf2264813a8daaa466b98119496ba85d4b9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346540"
---
# <a name="idebugdocumenthost-interface"></a>Interfaccia IDebugDocumentHost
Espone la funzionalità specifica dell'host, ad esempio di colorazione della sintassi, il debugger. Il `IDebugDocumentHelper::SetDebugDocumentHost` metodo accetta questa interfaccia come argomento.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugDocumentHost` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Restituisce un intervallo di caratteri che sono state aggiunte mediante `IDebugDocumentHelper::AddDeferredText`, in modo che il documento originale.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Restituisce gli attributi di testo per un blocco di testo del documento.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Notifica all'host che viene creato un nuovo contesto di documento e consente all'host facoltativamente restituire un oggetto che controlla il nuovo contesto.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Restituisce il percorso completo (incluso il nome del file) del file di origine del documento.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Restituisce il nome del documento, senza le informazioni sul percorso.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Notifica all'host che è stato salvato il file di origine del documento e che il relativo contenuto deve essere aggiornato.|