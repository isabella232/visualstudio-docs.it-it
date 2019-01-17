---
title: Interfaccia IDebugDocumentTextEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec89ae81d79fb7b0d822cafe2bf44f0ecd8ad81
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345659"
---
# <a name="idebugdocumenttextevents-interface"></a>Interfaccia IDebugDocumentTextEvents
Specifica eventi che indicano le modifiche per il documento di testo associato.  
  
> [!NOTE]
>  Il testo del documento cambia quando gli eventi in questa interfaccia incendi. Gestori di eventi possono recuperare il nuovo testo usando il `IDebugDocumentText` interfaccia.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugDocumentTextEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Indica che il documento sottostante è stata eliminata definitivamente e non è più valido|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Indica che il nuovo testo è stato aggiunto al documento|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Indica che il testo è stato rimosso dal documento.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Indica che il testo è stato sostituito.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Indica che gli attributi di testo associati all'intervallo di posizione di carattere sottostante sono stati modificati.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Indica che gli attributi del documento modificato.|