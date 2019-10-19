---
title: 'IDebugFormatter:: GetStringForVariant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576363"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Restituisce una stringa che rappresenta il valore VARIANT specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvar`  
 in VARIANTE da rappresentare come stringa.  
  
 `nRadix`  
 in Radice da usare per i valori numerici.  
  
 `pbstrValue`  
 out Stringa che rappresenta `pvar`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una stringa che rappresenta il valore Variant specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)