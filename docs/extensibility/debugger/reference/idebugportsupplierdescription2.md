---
title: Proprietà IDebugPortSupplierDescription2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724360"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Consente [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] all'interfaccia utente di visualizzare il testo all'interno della sezione **Informazioni sul trasporto** della finestra di dialogo Connetti a **processo.**

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai fornitori di porte.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugPortSupplierDescription2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDescrizione](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera i metadati di descrizione e descrizione per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
