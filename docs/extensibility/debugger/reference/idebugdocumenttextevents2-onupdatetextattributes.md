---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dc28591b8402792c5f25634da5e936ec03b2ecf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929309"
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
Notifica il pacchetto di debug che sono stati aggiornati gli attributi di testo nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT onUpdateTextAttributes(   
   TEXT_POSITION pos,  
   DWORD         dwNumToUpdate  
);  
```  
  
```csharp  
int onUpdateTextAttributes(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pos`  
 [in] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che indica dove sono stati aggiornati gli attributi di testo.  
  
 `dwNumToUpdate`  
 [in] Specifica il numero di caratteri del testo che sono stati aggiornati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)