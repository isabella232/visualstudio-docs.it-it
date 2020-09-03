---
title: 'IDebugField:: GetSize | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fded9abc006ff6a28e122f0a4b8d7fae5da997b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148925"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene le dimensioni in byte di un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSize`  
 out Restituisce la dimensione.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i campi hanno un tipo e tutti i tipi hanno una dimensione. Ad esempio, un campo con un tipo di byte ha una dimensione di 1 byte.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
