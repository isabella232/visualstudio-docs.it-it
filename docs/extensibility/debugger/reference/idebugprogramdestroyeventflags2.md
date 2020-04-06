---
title: Proprietà IDebugProgramDestroyEventFlags2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722496"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Consente a un motore di debug [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di eseguire l'override del comportamento predefinito dell'interfaccia utente quando si termina una sessione di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai motori di debug. È utile per gli host che potrebbero creare ed eliminare più programmi nel corso della durata di un processo.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugProgramDestroyEventFlags2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera i flag di eliminazione del programma.|

## <a name="remarks"></a>Osservazioni
 Il comportamento predefinito [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente consiste nel tornare alla modalità progettazione dopo che tutti i programmi hanno inviato un evento di eliminazione del programma. Questa interfaccia consente a un motore di debug di modificare tale comportamento.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
