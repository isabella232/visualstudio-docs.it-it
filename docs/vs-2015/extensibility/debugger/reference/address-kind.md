---
title: ADDRESS_KIND | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4b115457c69418039a752d2f50bd39d1ad80accf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531722"
---
# <a name="addresskind"></a>ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ADDRESS_KIND](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/address-kind).  
  
Specifica i tipi di indirizzi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Termini  
 ADDRESS_KIND_NATIVE  
 Un indirizzo nativo, rappresentato dal [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) struttura.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Un indirizzo non gestito rispetto a un `this` (`Me` in Visual Basic) puntatore e rappresentati dalle [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struttura.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Un indirizzo fisico non gestito, rappresentato dal [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) struttura.  
  
 ADDRESS_KIND_METHOD  
 Un metodo di una classe, rappresentato dal [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) struttura.  
  
 ADDRESS_KIND_FIELD  
 Un campo di una classe, rappresentato dal [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) struttura.  
  
 ADDRESS_KIND_LOCAL  
 L'indirizzo è per una variabile locale e viene rappresentato dal [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struttura.  
  
 ADDRESS_KIND_PARAM  
 Un parametro di metodo o funzione, rappresentato dal [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) struttura.  
  
 ADDRESS_KIND_ARRAYELEM  
 Un elemento della matrice rappresentato dal [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) struttura.  
  
 ADDRESS_KIND_RETVAL  
 Un valore restituito, rappresentato dal [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) struttura.  
  
## <a name="remarks"></a>Note  
 Il [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodo restituisce il [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura che contiene un'unione di possibili strutture, i [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura. Il `dwKind` campo le `DEBUG_ADDRESS_UNION` struttura contiene il `ADDRESS_KIND` valore e descrive come interpretare il campo di unione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)

