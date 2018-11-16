---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d7beb95a91f1b72a44046160359d171f3fcc4b3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754129"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrPortName`  
 [out] Restituisce il nome della porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia viene in genere passata da un pacchetto di debug (client) a un fornitore di porte (server) per ottenere una connessione a una porta. Sia il pacchetto di debug e il fornitore della porta sia consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, quindi il `IDebugPortRequest2::GetPortName` metodo ha informazioni sufficienti per stabilire la connessione. In caso contrario, interfacce aggiuntive possono essere fornite dal client, che può essere ottenuto tramite il server `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)

