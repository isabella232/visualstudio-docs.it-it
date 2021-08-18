---
title: Routing dei comandi nei pacchetti VSPackage | Microsoft Docs
description: Informazioni sul routing dei comandi nei pacchetti VSPackage e su come i comandi vengono instradati in base al contesto in cui vengono eseguiti in Visual Studio.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71c662fc268a5db121a7699e97e1fa03c364a785
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102818"
---
# <a name="command-routing-in-vspackages"></a>Routing dei comandi nei pacchetti VSPackage
Un comando viene indirizzato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in base al contesto in cui viene eseguito. Viene instradato dal contesto iniziale verso l'esterno al contesto globale.

## <a name="in-this-section"></a>Contenuto della sezione
- [Algoritmo di routing dei comandi](../../extensibility/internals/command-routing-algorithm.md)

 Descrive l'ordine di risoluzione del routing dei comandi.

- [Disponibilità dei comandi](../../extensibility/internals/command-availability.md)

 Viene illustrato il routing dei comandi.

- [Comandi e menu che usano assembly di interoperabilità](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Vengono illustrate le considerazioni relative al routing dei comandi tra codice gestito e COM.

## <a name="related-sections"></a>Sezioni correlate
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per determinare lo stato attivo del contesto di selezione dell'utente in una finestra.

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

 Spiega come creare un'interfaccia utente che include menu, barre degli strumenti e caselle combinate di comandi.
