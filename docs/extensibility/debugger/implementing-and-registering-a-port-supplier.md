---
title: Implementazione e registrazione di un fornitore di porte | Microsoft Docs
description: Informazioni su come implementare e registrare un fornitore di porte, che tiene traccia e fornisce le porte che gestiscono i processi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 151f14592e0987a16b3195944d3ef7ce0f972ea1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153472"
---
# <a name="implement-and-register-a-port-supplier"></a>Implementare e registrare un fornitore di porte
Il ruolo di un fornitore di porte è tenere traccia e fornire le porte, che a loro volta gestiscono i processi. Quando è necessario creare una porta, viene creata un'istanza del fornitore della porta usando CoCreate con il GUID del fornitore della porta (il gestore del debug di sessione [SDM] userà il fornitore della porta selezionato dall'utente o il fornitore di porte specificato dal sistema di progetto). SDM chiama quindi [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per verificare se è possibile aggiungere porte. Se è possibile aggiungere una porta, viene richiesta una nuova porta chiamando [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando una [classe IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort`restituisce una nuova porta rappresentata da [un'interfaccia IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Discussione
 Una porta viene creata da un fornitore di porte, associato a un computer o a un server di debug. Un server enumera i fornitori di porte tramite il[metodo EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) e un fornitore di porte enumera le porte tramite il [metodo EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 Oltre alla tipica registrazione COM, un fornitore di porte deve registrarsi con Visual Studio inserendo il clSID e il nome in percorsi specifici del Registro di sistema. Una funzione helper dell'SDK di debug denominata gestisce questa attività: viene chiamata una volta `SetMetric` per ogni elemento da registrare, quindi:

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

 Un fornitore di porte annulla la registrazione chiamando (un'altra funzione helper SDK di debug) una volta per ogni `RemoveMetric` elemento registrato, quindi:

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
> Gli [helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) e sono funzioni statiche definite in `SetMetric` `RemoveMetric` *dbgmetric.h* e compilate in *ad2de.lib.* Gli `metrictypePortSupplier` `metricCLSID` helper , e sono definiti anche `metricName` in *dbgmetric.h.*

 Un fornitore di porte può fornire il nome e il GUID rispettivamente tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId.](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)

## <a name="see-also"></a>Vedi anche
- [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
