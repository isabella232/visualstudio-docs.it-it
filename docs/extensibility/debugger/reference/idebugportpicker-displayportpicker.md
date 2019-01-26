---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e6f0a5b65e333f1f210735d8d61b39dac12b548
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962774"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Consente di visualizzare la finestra di dialogo specificata che consente all'utente di selezionare una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hwndParentDialog`  
 [in] Handle per la finestra di dialogo padre.  
  
 `pbstrPortId`  
 [out] Stringa dell'identificatore di porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un valore restituito pari `S_FALSE` (o valore restituito di `S_OK` con il `BSTR` impostata su `NULL`) indica che l'utente ha fatto clic **Annulla**.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)