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
ms.openlocfilehash: 75369df719b0cd140ce621e916215eb18cf30a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787619"
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
 [in] L'indice dell'elemento figlio del padre.  
  
 `dwCookie`  
 [in] Un valore definito dall'applicazione usato per associare la voce figlio con l'oggetto host.  
  
 `pszDelimiter`  
 [in] L'indirizzo del delimitatore end-di--blocco di script. Per l'analisi, l'host utilizza in genere un delimitatore (ad esempio due virgolette singole), per rilevare la fine del blocco di script.  
  
 Il delimitatore consente allo script di creazione motore per garantire la pre-elaborazione. Ad esempio, il motore potrebbe sostituire una virgoletta singola con due virgolette singole da usare come delimitatore. Il motore determina come viene utilizzato il delimitatore.  
  
 Se un delimitatore non contrassegna la fine del blocco di script, impostato su NULL.  
  
 `ppse`  
 [out] L'indirizzo di una variabile che riceve un puntatore al `IScriptEntry` interfaccia dell'istanza figlio.  
  
 Per la `IScriptNode` gli oggetti che rappresentano una pagina Web, questo parametro restituisce un `IScriptEntry` istanza che specifica un blocco di script.  
  
 Per la `IScriptEntry` gli oggetti che rappresentano un blocco di script, questo parametro restituisce un `IScriptEntry` istanza che specifica un oggetto funzione.  
  
 Per `IScriptEntry` gli oggetti che rappresentano una funzione dell'oggetto, questo metodo ha esito negativo.  
  
 Per `IScriptScriptlet` oggetti, questo metodo ha esito negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `IScriptNode` interfaccia rappresenta una pagina Web o dei relativi elementi. Il `IScriptEntry` interfaccia (che deriva da `IScriptNode`) rappresenta un blocco di script o un oggetto funzione. Il `IScriptScriptlet` interfaccia (che deriva da `IScriptEntry`) rappresenta un gestore eventi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)