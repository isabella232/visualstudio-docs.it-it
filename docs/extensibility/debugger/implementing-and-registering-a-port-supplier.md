---
title: Implementazione e registrazione di un fornitore di porte Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738526"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementare e registrare un fornitore di porte
Il ruolo di un fornitore di porte è quello di monitorare e fornire le porte, che a loro volta gestiscono i processi. Quando è necessario creare una porta, viene creata un'istanza del fornitore della porta utilizzando CoCreate con il GUID del fornitore della porta (il gestore di sessione di debug [SDM] utilizzerà il fornitore della porta selezionato dall'utente o il fornitore della porta specificato dal sistema del progetto). Il file SDM chiama quindi [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per verificare se è possibile aggiungere porte. Se è possibile aggiungere una porta, una nuova porta viene richiesta chiamando [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort`restituisce una nuova porta rappresentata da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia.

## <a name="discussion"></a>Discussione
 Una porta viene creata da un fornitore di porte, associato a un computer o a un server di debug. Un server enumera i fornitori di porte tramite il[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metodo e un fornitore di porta enumera le porte tramite il [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metodo.

 Oltre alla registrazione COM tipica, un fornitore di porta deve registrarsi con Visual Studio inserendo il CLSID e il nome in posizioni specifiche del Registro di sistema. Una funzione helper `SetMetric` SDK di debug denominata gestisce questa attività: viene chiamata una volta per ogni elemento da registrare, pertanto:A Debugging SDK helper function called handles this core: it is called once for each item to be registered, so:

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

 Un fornitore di porta `RemoveMetric` annulla la registrazione chiamando (un'altra funzione di supporto SDK di debug) una volta per ogni elemento che è stato registrato, pertanto:A port supplier unregisters to calling (another Debugging SDK helper function) once for each item that was registered, so:

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
> Gli helper SDK per `RemoveMetric` il [debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e sono funzioni statiche definite in *dbgmetric.h* e compilate in *ad2de.lib*. Gli `metrictypePortSupplier` `metricCLSID`helper `metricName` , e sono definiti anche in *dbgmetric.h*.

 Un fornitore di porta può fornire il proprio nome e GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.

## <a name="see-also"></a>Vedere anche
- [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fornitori portuali](../../extensibility/debugger/port-suppliers.md)
