---
title: Interfaccia IDebugDocumentText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 763678b08c22fe34ec6ffebbe670fb8b50af6576
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344395"
---
# <a name="idebugdocumenttext-interface"></a>Interfaccia IDebugDocumentText
Specifica l'accesso a una versione di solo testo del documento di debug. Questa interfaccia Usa le convenzioni seguenti:  
  
- Entrambe le posizioni dei caratteri e numeri di riga sono in base zero.  
  
- Le posizioni dei caratteri rappresentano gli offset di carattere; non rappresentare byte né gli offset di word. Per Win32, una posizione di carattere è un offset di Unicode.  
  
  Oltre ai metodi ereditati da `IDebugDocument`, il `IDebugDocumentText` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Restituisce gli attributi del documento.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Restituisce il numero di righe e numero di caratteri nel documento.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Restituisce la posizione del carattere corrispondente al primo carattere di una riga.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Restituisce il numero di riga e, facoltativamente, l'offset carattere nella riga che corrisponde alla posizione del carattere specificata.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Recupera i caratteri e/o gli attributi di carattere associati a un intervallo di posizione del carattere.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Restituisce l'intervallo di posizione del carattere corrispondente a un contesto di documento.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crea un oggetto di contesto di documento corrispondente all'intervallo di posizione del carattere specificato.|