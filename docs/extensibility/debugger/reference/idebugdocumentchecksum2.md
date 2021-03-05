---
description: Rappresenta un checksum per un documento di debug e consente di passare il checksum tra i componenti.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b39f381817cd98fd94b1c746cbdccde31e0b1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165566"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Rappresenta un checksum per un documento di debug e consente di passare il checksum tra i componenti.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia può essere implementata da qualsiasi componente che espone l'interfaccia [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Tuttavia, viene implementata principalmente dai motori di debug in modo che il checksum incorporato in un file di simboli (*. pdb) possa essere passato nuovamente all'IDE e utilizzato per la ricerca di un'origine.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugDocumentChecksum2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera il checksum del documento e l'identificatore dell'algoritmo dato il numero massimo di byte da usare.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
