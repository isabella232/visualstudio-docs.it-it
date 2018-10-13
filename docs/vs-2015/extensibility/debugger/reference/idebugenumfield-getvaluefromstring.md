---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
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
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c99c163eef122de65a15a43b5244ac2644f7618c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277006"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo restituisce il valore associato al nome di una costante di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Stringa che specifica il nome per il quale ottenere il valore. Si noti che per C++, questa è una stringa di caratteri "wide".  
  
 `pValue`  
 [out] Restituisce il valore numerico associato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, se il nome non fa parte di enumerazione o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è tra maiuscole e minuscole. Se è necessaria una ricerca tra maiuscole e minuscole (ad esempio, in un linguaggio, ad esempio Visual Basic in cui i nomi non sono tra maiuscole e minuscole), usare [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

