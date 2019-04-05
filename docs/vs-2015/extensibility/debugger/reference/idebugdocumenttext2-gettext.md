---
title: IDebugDocumentText2::GetText | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066c2c025fe7b1c83fb30cb3a0e1a7b61d8c2c41
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966171"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera il testo dalla posizione specificata nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```csharp  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pos`  
 [in] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura che indica la posizione del testo da recuperare.  
  
 `cMaxChars`  
 [in] Il numero massimo di caratteri del testo da recuperare.  
  
 `pText`  
 [in, out] Un puntatore a un buffer che deve essere compilato con il testo desiderato. Questo buffer deve essere in grado di contenere almeno `cMaxChars` numero di caratteri "wide".  
  
 `pcNumChars`  
 [out] Restituisce il numero di caratteri effettivamente recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="example"></a>Esempio  
 Questo esempio mostra come questo metodo può essere chiamato da codice c#.  
  
```csharp  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
