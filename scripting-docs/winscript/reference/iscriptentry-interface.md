---
title: Interfaccia IScriptEntry | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d7b33e2e5c90d5c489fe283575b4a2e45671f9a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349348"
---
# <a name="iscriptentry-interface"></a>Interfaccia IScriptEntry
Un oggetto che implementa il `IScriptEntry` interfaccia rappresenta un blocco di script o un oggetto funzione.  
  
 Oltre ai metodi ereditati da `IScriptNode`, il `IScriptEntry` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Restituisce il testo che corrisponde al corpo di un `IScriptEntry` blocco di script, blocco della funzione o scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Restituisce il nome dell'elemento che identifica un `IScriptEntry` oggetto.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Per le voci che rappresentano un singolo oggetto (ad esempio una funzione), restituisce il nome dell'oggetto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Restituisce la posizione iniziale e la lunghezza di una voce.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Restituisce informazioni sul tipo per un `IScriptEntry` oggetto funzione.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Restituisce il testo che corrisponde a un `IScriptEntry` blocco di script o codice sorgente che è contenuto in un `IScriptScriptlet` gestore dell'evento.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Imposta il testo presente nel corpo di un' `IScriptEntry` blocco di script o un `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Imposta il nome dell'elemento che identifica un `IScriptEntry` oggetto.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Per le voci che rappresentano un singolo oggetto (ad esempio una funzione), imposta il nome dell'oggetto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Set di informazioni sul tipo per un `IScriptEntry` oggetto funzione.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Imposta il testo che corrisponde a un `IScriptEntry` blocco di script o codice sorgente che è contenuto in un `IScriptScriptlet` gestore dell'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)