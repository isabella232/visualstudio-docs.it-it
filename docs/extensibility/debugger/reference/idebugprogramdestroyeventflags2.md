---
description: Consente a un motore di debug di eseguire l'override del comportamento predefinito Visual Studio'interfaccia utente quando si termina una sessione di debug.
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: af85e13acf6340cfa1be3f15ce72de551daf92e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071618"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Consente a un motore di debug di eseguire l'override del comportamento predefinito dell'interfaccia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utente quando si termina una sessione di debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai motori di debug. È utile per gli host che potrebbero creare ed eliminare più programmi nel corso della durata di un processo.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugProgramDestroyEventFlags2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera i flag di eliminazione del programma.|

## <a name="remarks"></a>Commenti
 Il comportamento predefinito dell'interfaccia utente è tornare alla modalità progettazione dopo che tutti i programmi hanno inviato un evento di eliminazione [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] programma. Questa interfaccia consente a un motore di debug di modificare tale comportamento.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
