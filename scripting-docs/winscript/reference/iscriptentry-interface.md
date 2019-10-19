---
title: Interfaccia IScriptEntry | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575387"
---
# <a name="iscriptentry-interface"></a>Interfaccia IScriptEntry
Un oggetto che implementa l'interfaccia `IScriptEntry` rappresenta un blocco di script o un oggetto funzione.  
  
 Oltre ai metodi ereditati da `IScriptNode`, l'interfaccia `IScriptEntry` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Restituisce il testo che corrisponde al corpo di un `IScriptEntry` blocco di script, di funzione o di scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Restituisce il nome dell'elemento che identifica un oggetto `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Per le voci che rappresentano un singolo oggetto, ad esempio una funzione, restituisce il nome dell'oggetto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Restituisce la posizione iniziale e la lunghezza di una voce.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Restituisce informazioni sul tipo per un oggetto `IScriptEntry` funzione.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Restituisce il testo che corrisponde a un blocco di script `IScriptEntry` o al codice sorgente contenuto in un gestore dell'evento `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Imposta il testo che si trova nel corpo di un `IScriptEntry` blocco di script o di un `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Imposta il nome dell'elemento che identifica un oggetto `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Per le voci che rappresentano un singolo oggetto, ad esempio una funzione, imposta il nome dell'oggetto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Imposta le informazioni sul tipo per un oggetto funzione `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Imposta il testo che corrisponde a un blocco di script `IScriptEntry` o al codice sorgente contenuto in un gestore dell'evento `IScriptScriptlet`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)