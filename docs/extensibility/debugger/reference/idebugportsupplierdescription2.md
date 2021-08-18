---
description: Consente all Visual Studio di interfaccia utente di visualizzare il testo all'interno della sezione Informazioni sul trasporto della finestra di dialogo Associa a processo .
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a8724b75e4360e8b7e4b097fa00f5f3ed112e735
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126791"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Consente [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] all'interfaccia utente di visualizzare il testo **all'interno della sezione Informazioni** sul trasporto della **finestra di dialogo** Associa a processo .

## <a name="syntax"></a>Sintassi

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai fornitori di porte.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugPortSupplierDescription2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descrizione e i metadati della descrizione per il fornitore della porta.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
