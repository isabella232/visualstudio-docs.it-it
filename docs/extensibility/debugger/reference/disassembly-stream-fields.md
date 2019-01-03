---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f7513ae0ac5094d51d4de2c7c4e0a49295110c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867475"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Specifica le informazioni da recuperare relative a un campo disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Membri  
 DSF_ADDRESS  
 Initialize/usare la `bstrAddress` campo.  
  
 DSF_ADDRESSOFFSET  
 Initialize/usare la `bstrAddressOffset` campo.  
  
 DSF_CODEBYTES  
 Initialize/usare la `bstrCodeBytes` campo.  
  
 DSF_OPCODE  
 Initialize/usare la `bstrOpCode` campo.  
  
 DSF_OPERANDS  
 Initialize/usare la `bstrOperands` campo.  
  
 DSF_SYMBOL  
 Initialize/usare la `bstrSymbol` campo.  
  
 DSF_CODELOCATIONID  
 Initialize/usare la `uCodeLocationId` campo.  
  
 DSF_POSITION  
 Initialize/usare la `posBeg` e `posEnd` campi.  
  
 DSF_DOCUMENTURL  
 Initialize/usare la `bstrDocumentUrl` campo.  
  
 DSF_BYTEOFFSET  
 Initialize/usare la `dwByteOffset` campo.  
  
 DSF_FLAGS  
 Initialize/usare la `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) campo.  
  
 DSF_OPERANDS_SYMBOLS  
 Includere i nomi dei simboli nel `bstrOperands` campo.  
  
 DSF_ALL  
 Specifica tutti i campi per il flusso di disassemblaggio.  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodo per indicare quali campi della [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struttura devono essere inizializzate.  
  
 Utilizzato per il `dwFields` membro del `DisassemblyData` struttura per indicare quali campi vengono usati e valido quando la struttura viene restituita.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)