---
description: Descrive vari attributi per un'interfaccia IDebugProperty2 o IDebugReference2.
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8137d5bad817478371fb57dcffc568db616949a1739e5d501ac4fe394d846d16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452446"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Descrive vari attributi per [un'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) o [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md) Membro della [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura .

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="members"></a>Members
 `DBG_ATTRIB_NONE`\
 Indica nessun attributo.

 `DBG_ATTRIB_ALL`\
 Indica tutti gli attributi.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Indica che il riferimento o la proprietà contiene figli.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Indica che è stato creato un ID per questo oggetto.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Indica che è possibile creare un ID per questo oggetto.

 `DBG_ATTRIB_VALUE_READONLY`\
 Indica che il valore è di sola lettura.

 `DBG_ATTRIB_VALUE_ERROR`\
 Indica che il valore è un errore.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Indica che la valutazione ha avuto un effetto collaterale.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Indica che questa proprietà è in realtà un contenitore di overload.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è booleano.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è booleano e `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` non è valido.

 `DBG_ATTRIB_VALUE_NAT`\
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è " not a *thing*" (NAT). NAT descrive un flag di registro nei processori Intel a 64 bit che indica eccezioni speculative posticipate.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Indica che il valore in è `DEBUG_PROPERTY_INFO::bstrValue` stato probabilmente espanso automaticamente.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Indica che si è verificata una valutazione.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` può essere rappresentato da una stringa non elaborata.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Indica che a questa proprietà è associato almeno un visualizzatore personalizzato.

 `DBG_ATTRIB_ACCESS_NONE`\
 Indica un oggetto che non ha accesso `public` al tipo , né `private` `protected` .

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Indica un oggetto con accesso pubblico.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Indica un oggetto con accesso privato.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Indica un oggetto con accesso protetto.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Indica un oggetto con accesso finale.

 `DBG_ATTRIB_ACCESS_ALL`\
 Maschera per estrarre gli attributi di accesso da `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Indica che non è specificato alcun tipo di archiviazione.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Indica l'archiviazione globale.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Indica l'archiviazione statica.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Indica l'archiviazione nel registro.

 `DBG_ATTRIB_STORAGE_ALL`\
 Maschera per estrarre gli attributi di archiviazione da `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_TYPE_NONE`\
 Indica che non è presente alcun modificatore di tipo.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Indica che il tipo di oggetto è virtuale.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Indica che il tipo di oggetto è costante.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Indica che il tipo di oggetto è sincronizzato.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Indica che il tipo di oggetto è volatile.

 `DBG_ATTRIB_TYPE_ALL`\
 Maschera per estrarre gli attributi di tipo da `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Indica che questo oggetto è un campo dati.

 `DBG_ATTRIB_METHOD`\
 Indica che questo oggetto è un metodo.

 `DBG_ATTRIB_PROPERTY`\
 Indica che questo oggetto è una proprietà.

 `DBG_ATTRIB_CLASS`\
 Indica che questo oggetto è una classe.

 `DBG_ATTRIB_BASECLASS`\
 Indica che questo oggetto è una classe di base.

 `DBG_ATTRIB_INTERFACE`\
 Indica che questo oggetto è un'interfaccia.

 `DBG_ATTRIB_INNERCLASS`\
 Indica che questo oggetto è una classe interna.

 `DBG_ATTRIB_MOSTDERIVED`\
 Indica che questo oggetto è il *più derivato di*. Il termine "*più derivato*" indica il tipo effettivo dell'oggetto e non il tipo del relativo riferimento.

 `DBG_ATTRIB_CHILD_ALL`\
 Indica una maschera da a `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Indica che all'oggetto sono associati più visualizzatori personalizzati.

## <a name="remarks"></a>Commenti

> [!NOTE]
> I valori in questa enumerazione non sono effettivamente definiti nell'assembly per C#. È invece necessario copiare le definizioni nel file di origine.

 Questi flag vengono usati anche per filtrare gli elementi figlio di un oggetto, ad esempio quando vengono passati come argomento a [EnumChildren.](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) I valori possono essere combinati con un bit per `OR` bit.

 Il flag indica di ottenere l'interfaccia `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) [dall'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) e chiamare [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) per un elenco di visualizzatori personalizzati.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
