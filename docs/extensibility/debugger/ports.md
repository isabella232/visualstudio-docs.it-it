---
title: Porte | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di una porta nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a504db1716eaad4fbf66c34985067310fada1fa1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710323"
---
# <a name="ports"></a>Porte
Nell'architettura del debugger, una *porta*:

- Contenitore per un set di processi in esecuzione in un server. Ad esempio, una porta può rappresentare una connessione a un dispositivo basato su Windows CE tramite un cavo seriale o a un computer non DCOM in rete. Una porta speciale, denominata porta locale, contiene tutti i processi in esecuzione nel computer locale.

- Può identificarsi in base al nome o all'identificatore.

- Può enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.

- È rappresentato da [un'interfaccia IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) creata passando un [argomento IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) ad [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce una porta predefinita che gestisce tutti Windows processi basati su processi, nativi e gestiti. Una porta personalizzata deve essere impostata per le connessioni con dispositivi esterni che non Windows basati su dispositivi. Per fornire tali porte personalizzate, è necessario configurare anche un fornitore di porte personalizzato.

## <a name="see-also"></a>Vedi anche
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
