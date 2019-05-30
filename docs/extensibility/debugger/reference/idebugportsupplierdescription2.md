---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae6491628888f682d61c94ae618bfad72837c845
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339886"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Consente il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente per visualizzare il testo all'interno di **informazioni sul trasporto** sezione del **Connetti a processo** nella finestra di dialogo.

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da fornitori di porte.

## <a name="methods"></a>Metodi
 Nella tabella seguente sono illustrati i metodi di `IDebugPortSupplierDescription2`.

|Metodo|Descrizione|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descrizione e una descrizione dei metadati per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll