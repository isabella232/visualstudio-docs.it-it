---
title: Proprietà Ports (Porte) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738315"
---
# <a name="ports"></a>Porte
Nell'architettura del debugger, una *porta*:

- È un contenitore per un set di processi in esecuzione su un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo basato su Windows CE tramite un cavo seriale o un computer non DCOM in rete. Una porta speciale, denominata porta locale, contiene tutti i processi in esecuzione nel computer locale.

- Può identificarsi in base al nome o all'identificatore.

- Può enumerare tutti i processi in esecuzione sulla porta e avviarli e terminarli.

- È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, che viene creata passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento a [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce una porta predefinita che gestisce tutti i processi basati su Windows, sia nativi che gestiti. È necessario configurare una porta personalizzata per le connessioni con dispositivi esterni non basati su Windows. Per fornire tali porte personalizzate, è necessario impostare anche un fornitore di porte personalizzato.

## <a name="see-also"></a>Vedere anche
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
