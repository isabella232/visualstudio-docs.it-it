---
description: Ottiene informazioni estese per la proprietà.
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 996e470d3ee61efde790d95adc367d9b1b86688c4df64cefae9384e0a657d050
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449053"
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
[out] Restituisce un `VARIANT` oggetto (C++) o (C#) che può essere usato per recuperare le informazioni sulle proprietà estese. Ad esempio, questo parametro potrebbe restituire un'interfaccia su cui è possibile eseguire `IUnknown` query per [un'interfaccia IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Per ulteriori informazioni, vedere Note.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore. Restituisce `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se non sono presenti informazioni estese da recuperare.

## <a name="remarks"></a>Commenti
 Questo metodo esiste allo scopo di recuperare informazioni che non si prestano al recupero chiamando il [metodo GetPropertyInfo.](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

 I GUID seguenti vengono in genere riconosciuti da questo metodo (i valori GUID vengono specificati per C# perché il nome non è disponibile in alcun assembly). È possibile creare GUID aggiuntivi per uso interno.

|Nome|GUID|Descrizione|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Restituisce `IUnknown` un'interfaccia al documento. In genere, [l'interfaccia IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) può essere ottenuta da questa `IUnknown` interfaccia.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Restituisce `IUnknown` un'interfaccia al contesto del documento. In genere, [l'interfaccia IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) può essere ottenuta da questa `IUnknown` interfaccia.|
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Restituisce una stringa contenente il CLSID di un visualizzatore personalizzato, in genere implementato da un analizzatore di espressioni.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Restituisce un numero a 32 bit che rappresenta il numero di slot desiderato se questa proprietà rappresenta un indirizzo locale del codice gestito.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Restituisce una stringa contenente la firma della variabile associata all'oggetto proprietà.|

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
