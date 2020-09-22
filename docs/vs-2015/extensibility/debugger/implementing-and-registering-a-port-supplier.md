---
title: Implementazione e registrazione di un fornitore di porte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840044"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementazione e registrazione di un fornitore di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il ruolo di un fornitore di porte è quello di rilevare e fornire porte, che a loro volta gestiscono i processi. Nel momento in cui è necessario creare una porta, viene creata un'istanza del fornitore della porta utilizzando CoCreate con il GUID del fornitore della porta (gestione debug sessione [SDM] utilizzerà il fornitore della porta selezionato dall'utente o il fornitore della porta specificato dal sistema del progetto). SDM chiamerà quindi [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per verificare se è possibile aggiungere porte. Se è possibile aggiungere una porta, viene richiesta una nuova porta chiamando [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passandogli un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort` restituirà una nuova porta rappresentata da un'interfaccia [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Discussione  
 Una porta viene creata da un fornitore di porte, che a sua volta è associato a un computer o a un server di debug. Un server può enumerare i propri fornitori di porte tramite il metodo[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) e un fornitore di porte può enumerare le relative porte tramite il metodo [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 Oltre alla registrazione COM tipica, è necessario che un fornitore di porte si registri con Visual Studio inserendo il relativo CLSID e nome in specifici percorsi del registro di sistema. Una funzione helper SDK di debug denominata `SetMetric` gestisce questa operazione di routine: viene chiamata una volta per ogni elemento da registrare, quindi:  
  
```cpp#  
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
  
```cpp#  
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
> Gli [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` sono funzioni statiche definite in dbgmetric. h e compilate in ad2de. lib. Gli `metrictypePortSupplier` `metricCLSID` Helper, e `metricName` sono definiti anche in dbgmetric. h.  
  
 Un fornitore di porte può fornire il nome e il GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
