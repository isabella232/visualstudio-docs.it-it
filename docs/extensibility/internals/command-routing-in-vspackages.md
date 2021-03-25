---
title: Routing di comandi nei pacchetti VSPackage | Microsoft Docs
description: Informazioni sul routing dei comandi nei pacchetti VSPackage e sul modo in cui i comandi vengono instradati in base al contesto in cui vengono eseguiti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ab5e7989fdeb46592f38cb7e55854885e076d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057299"
---
# <a name="command-routing-in-vspackages"></a>Routing di comandi nei pacchetti VSPackage
Un comando viene instradato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] base al contesto in cui viene eseguito. Viene indirizzato dal contesto iniziale verso il contesto globale.

## <a name="in-this-section"></a>Contenuto della sezione
- [Algoritmo di routing del comando](../../extensibility/internals/command-routing-algorithm.md)

 Descrive l'ordine di risoluzione del routing dei comandi.

- [Disponibilità comando](../../extensibility/internals/command-availability.md)

 Viene illustrato il routing del comando.

- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Vengono illustrate alcune considerazioni relative al routing di comandi tra codice gestito e COM.

## <a name="related-sections"></a>Sezioni correlate
- [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per determinare lo stato attivo del contesto di selezione dell'utente in una finestra.

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.
