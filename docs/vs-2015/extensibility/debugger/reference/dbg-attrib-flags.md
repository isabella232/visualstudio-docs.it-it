---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74694c903040b278ed8864b46756cac66381405a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839432"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vengono descritti i vari attributi per un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o un'interfaccia [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Membro della struttura [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```csharp  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## <a name="members"></a>Membri  
 DBG_ATTRIB_NONE  
 Indica nessun attributo.  
  
 DBG_ATTRIB_ALL  
 Indica tutti gli attributi.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 Indica che il riferimento o la proprietà contiene figli.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 Indica che è stato creato un ID per questo oggetto.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 Indica che è possibile creare un ID per questo oggetto.  
  
 DBG_ATTRIB_VALUE_READONLY  
 Indica che il valore è di sola lettura.  
  
 DBG_ATTRIB_VALUE_ERROR  
 Indica che il valore è un errore.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 Indica che la valutazione ha avuto un effetto collaterale.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 Indica che questa proprietà è effettivamente un contenitore di overload.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è booleano.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è booleano e `TRUE` .  
  
 DBG_ATTRIB_VALUE_INVALID  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` non è valido.  
  
 DBG_ATTRIB_VALUE_NAT  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è "*not a Thing*" (NAT). NAT descrive un flag di registro nei processori Intel a 64 bit che indica eccezioni speculative posticipate.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è stato eventualmente espanso automaticamente.  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 Indica il timeout di una valutazione.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` può essere rappresentato da una stringa non elaborata.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 Indica che a questa proprietà è associato almeno un visualizzatore personalizzato.  
  
 DBG_ATTRIB_ACCESS_NONE  
 Indica un oggetto che non dispone `public` di `private` accesso di tipo,, o `protected` .  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 Indica un oggetto con accesso pubblico.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 Indica un oggetto con accesso privato.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 Indica un oggetto con accesso protetto.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 Indica un oggetto con accesso finale.  
  
 DBG_ATTRIB_ACCESS_ALL  
 Maschera da cui estrarre gli attributi di accesso `DBG_ATTRIB_FLAGS` .  
  
 DBG_ATTRIB_STORAGE_NONE  
 Indica che non è stato specificato alcun tipo di archiviazione.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 Indica l'archiviazione globale.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 Indica l'archiviazione statica.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 Indica l'archiviazione nel registro.  
  
 DBG_ATTRIB_STORAGE_ALL  
 Maschera da cui estrarre gli attributi di archiviazione `DBG_ATTRIB_FLAGS` .  
  
 DBG_ATTRIB_TYPE_NONE  
 Indica che non è presente alcun modificatore di tipo.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 Indica che il tipo di oggetto è virtuale.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 Indica che il tipo di oggetto è costante.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 Indica che il tipo di oggetto è sincronizzato.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 Indica che il tipo di oggetto è volatile.  
  
 DBG_ATTRIB_TYPE_ALL  
 Maschera da cui estrarre gli attributi del tipo `DBG_ATTRIB_FLAGS` .  
  
 DBG_ATTRIB_DATA  
 Indica che l'oggetto è un campo dati.  
  
 DBG_ATTRIB_METHOD  
 Indica che questo oggetto è un metodo.  
  
 DBG_ATTRIB_PROPERTY  
 Indica che l'oggetto è una proprietà.  
  
 DBG_ATTRIB_CLASS  
 Indica che l'oggetto è una classe.  
  
 DBG_ATTRIB_BASECLASS  
 Indica che l'oggetto è una classe di base.  
  
 DBG_ATTRIB_INTERFACE  
 Indica che l'oggetto è un'interfaccia.  
  
 DBG_ATTRIB_INNERCLASS  
 Indica che l'oggetto è una classe interna.  
  
 DBG_ATTRIB_MOSTDERIVED  
 Indica che l'oggetto è "*più derivato*". Il termine "*più derivato*" indica il tipo effettivo dell'oggetto, non il tipo di riferimento.  
  
 DBG_ATTRIB_CHILD_ALL  
 Indica una maschera da `DBG_ATTRIB_DATA` a `DBG_ATTRIB_MOSTDERIVED` .  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 Indica che all'oggetto sono associati più visualizzatori personalizzati.  
  
## <a name="remarks"></a>Commenti  
  
> [!NOTE]
> I valori in questa enumerazione non sono effettivamente definiti nell'assembly per C#. Al contrario, è necessario copiare le definizioni nel file di origine.  
  
 Questi flag vengono usati anche per filtrare gli elementi figlio di un oggetto, ad esempio, quando viene passato come argomento a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). I valori possono essere combinati con un bit per bit `OR` .  
  
 Il `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` flag indica a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] di ottenere l'interfaccia [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dall'interfaccia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) e chiamare [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) per un elenco di visualizzatori personalizzati.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
