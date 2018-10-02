---
title: Implementazione e registrazione di un fornitore di porte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe8e5cac0b1737d7c3dbd7e9301e0ca25d778db4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531179"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implementazione e registrazione di un fornitore di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [implementazione e registrazione di un fornitore di porte](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-and-registering-a-port-supplier).  
  
Il ruolo di un fornitore di porte consiste nel tenere traccia e specificare le porte, che a sua volta la gestione dei processi. Al momento che è necessario creare una porta, il fornitore della porta viene creata un'istanza usando CoCreate con GUID del fornitore della porta (gestore di sessione di debug [SDM] userà il fornitore della porta selezionato dall'utente o il fornitore della porta specificato dal sistema del progetto). Verrà quindi chiamato il modello SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) per vedere se è possono aggiungere tutte le porte. Se è possibile aggiungere una porta, viene richiesta una nuova porta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) e passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) che descrive la porta. `AddPort` Restituisce una nuova porta rappresentata da un' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia.  
  
## <a name="discussion"></a>Discussione  
 Viene creata una porta da un fornitore di porte, che a sua volta associato a un server di macchina o di debug. Un server possa enumerare i suoi fornitori porta tramite il[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) metodo e un fornitore di porte può enumerare le relative porte tramite il [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) (metodo).  
  
 Oltre la normale registrazione COM, un fornitore di porte deve registrarsi con Visual Studio, inserendo il CLSID e il nome in posizioni specifiche del Registro di sistema. Chiamare una funzione helper Debugging SDK `SetMetric` gestisce questo compito ingrato: viene chiamato una volta per ogni elemento da registrare, in questo modo:  
  
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
  
 Un fornitore di porte Annulla la registrazione di se stessa chiamando `RemoveMetric` (un'altra funzione di supporto Debugging SDK) una volta per ogni elemento che è stato registrato, in questo modo:  
  
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
>  Il [helper SDK for Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` e `RemoveMetric` sono funzioni statiche definite in dbgmetric.h e compilati in ad2de.lib. Il `metrictypePortSupplier`, `metricCLSID`, e `metricName` helper sono definiti anche nel dbgmetric.h.  
  
 Un fornitore di porte può fornire il nome e GUID tramite i metodi [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) e [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), rispettivamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Helper SDK per eseguire il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)

