---
title: Proprietà IDebugProperty2::GetExtendedInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721483"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Ottiene informazioni estese per la proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Parametri
`guidExtendedInfo`\
[in] GUID che determina il tipo di informazioni estese da recuperare. Per ulteriori informazioni, vedere Note.

`pExtendedInfo`\
[fuori] Restituisce `VARIANT` un oggetto (C) o (C) che può essere utilizzato per recuperare le informazioni sulle proprietà estese. Ad esempio, questo parametro potrebbe restituire un'interfaccia `IUnknown` che può essere eseguita una query per un [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaccia. Per ulteriori informazioni, vedere Note.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore. Restituisce `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se non sono presenti informazioni estese da recuperare.

## <a name="remarks"></a>Osservazioni
 Questo metodo esiste allo scopo di recuperare informazioni che non si prestano al recupero chiamando il [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo.

 I GUID seguenti vengono in genere riconosciuti da questo metodo (i valori GUID vengono specificati per C , poiché il nome non è disponibile in alcun assembly). È possibile creare GUID aggiuntivi per uso interno.

|Nome|GUID|Descrizione|
|----------|----------|-----------------|
|guidDocument (documento guid)|3f98de84-fee9-11d0-b47f-00a0244a1dd2|Restituisce `IUnknown` un'interfaccia al documento. In genere, il [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) interfaccia `IUnknown` può essere ottenuta da questa interfaccia.|
|guidCodeContext|E2fc65e-56ce-11d1-b528-00aax004a8797|Restituisce `IUnknown` un'interfaccia al contesto del documento. In genere, il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia `IUnknown` può essere ottenuta da questa interfaccia.|
|guidCustomViewerSupported|D9c9da31-ffbe-4eeb-9186-23121e3c088c|Restituisce una stringa contenente il CLSID di un visualizzatore personalizzato, in genere implementato da un analizzatore di espressioni.|
|guidExtendedInfoSlot (informazioni in stato di contatto)|6df235ad-82c6-4292-9c97-7389770bc42f|Restituisce un numero a 32 bit che rappresenta il numero di slot desiderato se questa proprietà rappresenta un indirizzo locale del codice gestito.|
|guidExtendedInfoSignature (firma di guidExtendedInfo|B5fb6d46-f805-417f-96a3-8ba737073ffd|Restituisce una stringa contenente la firma della variabile associata all'oggetto proprietà.|

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
