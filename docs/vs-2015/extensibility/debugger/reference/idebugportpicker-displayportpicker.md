---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58963987"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente di visualizzare la finestra di dialogo specificata che consente all'utente di selezionare una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
