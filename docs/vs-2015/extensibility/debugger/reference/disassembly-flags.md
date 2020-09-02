---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159308"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica i flag per il disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Membri  
 DF_DOCUMENTCHANGE  
 Indica che l'istruzione si trova in un documento diverso rispetto a quello precedente.  
  
 DF_DISABLED  
 Indica che l'istruzione non verrà eseguita.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica che questa istruzione è una delle istruzioni seguenti da eseguire (possono essere presenti più di uno).  
  
 DF_DATA  
 Indica che l'istruzione è effettivamente dati (non codice).  
  
 DF_HASSOURCE  
 Indica che l'istruzione contiene l'origine. Alcune istruzioni, ad esempio la profilatura o il Garbage Collection codice, non hanno origine corrispondente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica che `bstrDocumentUrl` il campo contiene dati di checksum dopo l'URL del documento. Vedere la sezione Osservazioni per la struttura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) per la modalità di archiviazione dei dati di checksum.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzato come `dwFlags` membro della struttura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Questi flag possono essere combinati con un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
