---
title: Interfaccia IDebugDocumentHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7322ea5e2026ff3f4491ed1106dceb97a5f11c73
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153461"
---
# <a name="idebugdocumenthelper-interface"></a>Interfaccia IDebugDocumentHelper
Fornire implementazioni per molte interfacce necessarie per l'hosting smart, ad esempio la `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, e `IDebugDocumentTextEvents` interfacce.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugDocumentHelper` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Inizializza un helper di documenti di debug con un nome e gli attributi iniziali.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Questo documento aggiunto all'albero del documento.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Rimuove l'albero del documento di questo documento.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Aggiunge una stringa Unicode alla fine di questo documento.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Aggiunge una stringa DBCS alla fine di questo documento.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Imposta il `IDebugDocumentHost` per questo documento.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Notifica dell'helper che il testo specificato è disponibile, ma non fornisce i caratteri.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Indica all'helper che un determinato intervallo di caratteri è un blocco di script gestito dal motore di script specificato.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Imposta gli attributi predefiniti da utilizzare per il testo che non sia in un blocco di script.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Imposta gli attributi in un intervallo di testo.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Imposta il nome lungo del documento.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Imposta il nome breve per il documento.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Imposta gli attributi per questo documento.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Restituisce il nodo di debug dell'applicazione corrispondente a questo documento.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Recupera l'intervallo di caratteri e il motore di script corrispondente a un blocco di script.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Crea un nuovo contesto di documento di debug.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Porta in questo documento verso l'alto nel debugger interfaccia utente.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Offre un contesto di questo documento verso l'alto nell'interfaccia utente del debugger.|