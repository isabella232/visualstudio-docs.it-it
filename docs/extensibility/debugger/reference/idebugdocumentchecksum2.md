---
description: Rappresenta un checksum per un documento di debug e consente di passare il checksum tra i componenti.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3bcd872ed06fac90d48bc773250fd007d3ed1d21e8b4714876d62e038df2f813
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433996"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Rappresenta un checksum per un documento di debug e consente di passare il checksum tra i componenti.

## <a name="syntax"></a>Sintassi

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia può essere implementata da qualsiasi componente che espone [l'interfaccia IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Tuttavia, viene implementata principalmente dai motori di debug in modo che il checksum incorporato in un file di simboli (*.pdb) possa essere passato nuovamente all'IDE e usato durante la ricerca di un'origine.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugDocumentChecksum2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera il checksum del documento e l'identificatore dell'algoritmo in base al numero massimo di byte da usare.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
