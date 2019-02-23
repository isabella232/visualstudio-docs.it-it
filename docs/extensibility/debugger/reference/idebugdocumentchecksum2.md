---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b40129cb8623e6ea68babe2c480da4e4d4198f3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685586"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Rappresenta un checksum per un documento di debug e consente di passare il valore di checksum tra componenti.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia può essere implementata da qualsiasi componente che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia. Tuttavia, viene principalmente implementato da motori di debug in modo che il valore di checksum incorporato in un file di simboli (*. pdb) può essere passato all'IDE e utilizzato durante la ricerca di un'origine.

## <a name="methods"></a>Metodi
 Nella tabella seguente sono illustrati i metodi di `IDebugDocumentChecksum2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera l'identificatore di algoritmo e del documento dato il numero massimo di byte da usare.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll