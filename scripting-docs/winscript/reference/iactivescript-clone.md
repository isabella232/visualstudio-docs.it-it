---
title: 'IActiveScript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093665"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona il motore di script corrente (meno qualsiasi stato corrente dell'esecuzione), restituendo un motore di script caricato che non dispone di alcun sito nel thread corrente. Le proprietà di questo nuovo motore di scripting sono identiche alle proprietà del che motore di script originale sarebbe se si sono stati eseguito la transizione allo stato inizializzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppscript`  
 [out] Indirizzo di una variabile che riceve un puntatore per il [IActiveScript](../../winscript/reference/iactivescript.md) interfaccia del motore di scripting clonato. L'host deve creare un sito e si chiama il [IActiveScript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) metodo sul nuovo motore di scripting affinché questa risulti in stato non inizializzato e, di conseguenza, utilizzabile.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è supportato.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Il `IActiveScript::Clone` metodo è un'ottimizzazione dei `IPersist*::Save`, `CoCreateInstance`, e `IPersist*::Load`, in modo che lo stato del motore di script nuovo deve essere lo stesso come se lo stato del motore di script originale sono stato salvato e caricato in un nuovo motore di scripting. Gli elementi denominati vengono duplicati nel motore di scripting clonato, ma sono dimenticati di puntatori a oggetti specifici per ogni elemento e possono essere ottenuti con la [iactivescriptsite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) (metodo). In questo modo un modello a oggetti identici con punti di ingresso per ogni thread (un modello di apartment) da utilizzare.  
  
 Questo metodo viene utilizzato per gli host server multithreading che è possono eseguire più istanze dello stesso script. Può restituire il motore di scripting `E_NOTIMPL`, nel qual caso l'host può ottenere lo stesso risultato per duplicare lo stato permanente e la creazione di una nuova istanza del motore di script con un `IPersist*` interfaccia.  
  
 Questo metodo può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)