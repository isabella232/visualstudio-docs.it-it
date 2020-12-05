---
title: Porte | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di una porta nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f13ca62f841525ef91ac7d66b67c09da54cabeb3
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606559"
---
# <a name="ports"></a>Porte
Nell'architettura del debugger, una *porta*:

- È un contenitore per un set di processi in esecuzione in un server. Una porta, ad esempio, potrebbe rappresentare una connessione a un dispositivo basato su Windows CE da un cavo seriale o a un computer non DCOM connesso in rete. Una porta speciale, denominata porta locale, contiene tutti i processi in esecuzione nel computer locale.

- Può identificare se stesso in base al nome o all'identificatore.

- Può enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.

- È rappresentato da un'interfaccia [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , che viene creata passando un argomento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) a [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, sia nativi che gestiti. È necessario configurare una porta personalizzata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, è necessario configurare anche un fornitore di porte personalizzato.

## <a name="see-also"></a>Vedere anche
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
