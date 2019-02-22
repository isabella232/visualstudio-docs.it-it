---
title: Routing di comandi in pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5749875a440a3122a06b81ae9d721e75ded6202c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641299"
---
# <a name="command-routing-in-vspackages"></a>Routing dei comandi nei pacchetti VSPackage
Un comando viene instradato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basato sul contesto in cui viene eseguita. Viene indirizzato dal contesto iniziale verso l'esterno al contesto globale.

## <a name="in-this-section"></a>Contenuto della sezione
- [Algoritmo di routing di comandi](../../extensibility/internals/command-routing-algorithm.md)

 Descrive l'ordine della risoluzione di routing dei comandi.

- [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)

 Viene illustrato il routing di comandi.

- [I comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Vengono fornite informazioni sul routing di comandi tra codice gestito e COM.

## <a name="related-sections"></a>Sezioni correlate
- [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per come è possibile determinare lo stato attivo contesto di selezione dell'utente in una finestra.

- [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.