---
title: 'IPerPropertyBrowsing2:: GetDisplayString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571460"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Ottiene una stringa per visualizzare i tipi che non sono intrinsecamente visualizzabili il testo restituito è un nome che descrive la proprietà e può essere visualizzato nell'interfaccia utente del chiamante.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dispid`  
 in Identificatore di invio della proprietà il cui nome visualizzato è richiesto.  
  
 `pBstr`  
 out Puntatore al `BSTR` contenente il nome visualizzato per la proprietà identificata da `dispID`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `HRESULT` valido, in genere `S_OK`.  
  
## <a name="remarks"></a>Note  
 La stringa restituita non è un valore valido della proprietà. Si tratta semplicemente di una visualizzazione di stringa della proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)