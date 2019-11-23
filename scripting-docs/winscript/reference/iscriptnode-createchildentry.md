---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573608"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Aggiunge un'istanza figlio di `IScriptEntry`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `isn`  
 in Indice dell'elemento figlio nell'elemento padre.  
  
 `dwCookie`  
 in Valore definito dall'applicazione utilizzato per associare la voce figlio all'oggetto host.  
  
 `pszDelimiter`  
 in Indirizzo del delimitatore di blocco di fine dello script. Per l'analisi, l'host usa in genere un delimitatore, ad esempio due virgolette singole, per rilevare la fine del blocco di script.  
  
 Il delimitatore consente al motore di creazione di script di fornire la pre-elaborazione. Ad esempio, il motore potrebbe sostituire una virgoletta singola con due virgolette singole da utilizzare come delimitatore. Il motore determina il modo in cui viene utilizzato il delimitatore.  
  
 Impostare su NULL se un delimitatore non contrassegna la fine del blocco di script.  
  
 `ppse`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `IScriptEntry` dell'istanza figlio.  
  
 Per `IScriptNode` oggetti che rappresentano una pagina Web, questo parametro restituisce un'istanza di `IScriptEntry` che specifica un blocco di script.  
  
 Per `IScriptEntry` oggetti che rappresentano un blocco di script, questo parametro restituisce un'istanza di `IScriptEntry` che specifica un oggetto funzione.  
  
 Per `IScriptEntry` oggetti che rappresentano un oggetto funzione, questo metodo ha esito negativo.  
  
 Per `IScriptScriptlet` oggetti, questo metodo ha esito negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'interfaccia `IScriptNode` rappresenta una pagina Web o i relativi elementi. L'interfaccia `IScriptEntry` (derivata da `IScriptNode`) rappresenta un blocco di script o un oggetto funzione. L'interfaccia `IScriptScriptlet` (derivata da `IScriptEntry`) rappresenta un gestore eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)