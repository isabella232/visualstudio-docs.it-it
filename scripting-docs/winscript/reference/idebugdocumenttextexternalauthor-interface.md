---
title: Interfaccia IDebugDocumentTextExternalAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor interface
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb7b09beb38fcdfb2a139fa385119cf9f76d77ae
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344214"
---
# <a name="idebugdocumenttextexternalauthor-interface"></a>Interfaccia IDebugDocumentTextExternalAuthor
Consente gli editor esterni modificare in modo sicuro i documenti di debugger basate su file inviando una notifica del documento quando viene modificato il file di origine.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugDocumentTextExternalAuthor` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|Restituisce il nome di file e percorso completo del documento.|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|Restituisce il nome del documento senza informazioni sul percorso.|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|Notifica all'host che l'origine del documento è stato modificato.|