---
title: Interfaccia IDebugDocumentTextExternalAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 60fb0d68d8052990fcc1783f86d0213b714dbfc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978485"
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