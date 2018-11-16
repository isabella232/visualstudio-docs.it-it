---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
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
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afd29868fa0f1e8c766e5ed1504c6e5152b9118f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776434"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene le informazioni sulla lingua per il contesto di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```csharp  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrLanguage`  
 [in, out] Restituisce una stringa che contiene il nome del linguaggio, ad esempio "C++".  
  
 `pguidLanguage`  
 [in, out] Restituisce il GUID per la lingua del contesto del codice, ad esempio, `guidCPPLang`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Almeno uno dei parametri deve restituire un valore diverso da null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

