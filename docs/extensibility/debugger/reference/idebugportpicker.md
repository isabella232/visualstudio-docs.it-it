---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 845e197b186d462b74aaf8cf3cd7218e4606dfc7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716545"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Rappresenta un'interfaccia utente personalizzata per la selezione della porta.

## <a name="syntax"></a>Sintassi

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da fornitori di porte. Un fornitore di porte viene definito il selettore porta esporlo come CLSID e scegliendo il `metricPortPickerCLSID` metrica a CLSID esposto.

## <a name="methods"></a>Metodi
 Nella tabella seguente sono illustrati i metodi di `IDebugPortPicker`.

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Consente di visualizzare la finestra di dialogo specificata che consente all'utente di selezionare una porta.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Imposta il provider del servizio.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll