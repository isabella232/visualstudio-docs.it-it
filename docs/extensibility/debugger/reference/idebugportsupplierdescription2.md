---
description: Consente all'interfaccia utente di Visual Studio di visualizzare il testo nella sezione informazioni di trasporto della finestra di dialogo Connetti a processo.
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba3cd07bb84843ff4d2531cdde63ab9e671f961
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071922"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Consente all' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente di visualizzare il testo nella sezione **informazioni di trasporto** della finestra di dialogo **Connetti a processo** .

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai fornitori di porte.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugPortSupplierDescription2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera i metadati della descrizione e della descrizione per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
