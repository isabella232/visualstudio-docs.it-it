---
title: Implementazione e registrazione di un fornitore di porte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738526"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementare e registrare un fornitore di porte
Il ruolo di un fornitore di porte è quello di rilevare e fornire porte, che a loro volta gestiscono i processi. Quando è necessario creare una porta, viene creata un'istanza del fornitore della porta mediante CoCreate con il GUID del fornitore della porta (gestione debug della sessione [SDM] utilizzerà il fornitore della porta selezionato dall'utente o il fornitore della porta specificato dal sistema del progetto). Il SDM chiama quindi [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per verificare se è possibile aggiungere porte. Se è possibile aggiungere una porta, viene richiesta una nuova porta chiamando [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passandogli un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort` Restituisce una nuova porta rappresentata da un'interfaccia [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .

## <a name="discussion"></a>Discussione
 Una porta viene creata da un fornitore di porte, associato a un computer o a un server di debug. Un server enumera i propri fornitori di porte tramite il metodo[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) e un fornitore di porte enumera le relative porte tramite il metodo [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .

 Oltre alla registrazione COM tipica, è necessario che un fornitore di porte si registri con Visual Studio inserendo il relativo CLSID e nome in specifici percorsi del registro di sistema. Una funzione helper SDK di debug denominata `SetMetric` gestisce questa operazione di routine: viene chiamata una volta per ogni elemento da registrare, quindi:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Un fornitore di porte Annulla la registrazione chiamando `RemoveMetric` (un'altra funzione helper SDK di debug) una volta per ogni elemento registrato, quindi:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Gli [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` sono funzioni statiche definite in *dbgmetric. h* e compilate in *ad2de. lib*. Gli `metrictypePortSupplier` `metricCLSID` Helper, e `metricName` sono definiti anche in *dbgmetric. h*.

 Un fornitore di porte può fornire il nome e il GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.

## <a name="see-also"></a>Vedere anche
- [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
