---
title: Gerarchie e selezione | Microsoft Docs
description: Informazioni sul modo in cui Visual Studio gestisce le gerarchie, ad esempio i progetti, e il modo in cui usa il contesto di selezione per determinare gli elementi visualizzati dall'utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04f433e3da45e10d2b1721ac13254856489d2d0a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480421"
---
# <a name="hierarchies-and-selection"></a>Gerarchie e selezione
Quando si Personalizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è necessario comprendere il modo in cui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le gerarchie, ad esempio i progetti e il modo in cui usa il contesto di selezione per determinare gli elementi visualizzati dall'utente. In questa sezione vengono illustrati i concetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie e selezione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Descrive le gerarchie di progetto e il concetto generale di gerarchie.

- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Viene descritto il modo in cui il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) mantiene le informazioni sugli oggetti attualmente attivi dell'utente e consente ai VSPackage di tenere traccia della valuta.

- [Oggetti contesto selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per determinare lo stato attivo del contesto di selezione dell'utente in una finestra.

- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)

 Viene illustrato il modo in cui la funzionalità disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si basa sul contesto di selezione corrente dell'utente e sul contesto dell'IDE generale.

## <a name="related-sections"></a>Sezioni correlate
- [Architettura di tipi di progetto](../../extensibility/internals/project-types-architecture.md)

 Fornisce informazioni tecniche dettagliate sui tipi di progetto.
