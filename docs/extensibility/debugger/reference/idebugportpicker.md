---
title: Proprietà IDebugPortPicker . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724839"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Rappresenta un'interfaccia utente personalizzata per la selezione della porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai fornitori di porte. Un fornitore di porte definisce il proprio selettore di porta `metricPortPickerCLSID` esponendolo come CLSID e puntando la metrica al CLSID esposto.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugPortPicker`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Visualizza la finestra di dialogo specificata che consente all'utente di selezionare una porta.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Imposta il provider di servizi.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
