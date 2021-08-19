---
title: Gerarchie e selezione | Microsoft Docs
description: Informazioni su Visual Studio le gerarchie, ad esempio i progetti, e su come usa il contesto di selezione per determinare ciò che viene visualizzato all'utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f44c9449181734299e6fb46ce2b76bab1d8d453a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063343"
---
# <a name="hierarchies-and-selection"></a>Gerarchie e selezione
Quando si personalizza , è necessario comprendere come gestisce le gerarchie, ad esempio i progetti, e come usa il contesto di selezione per determinare ciò che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene visualizzato all'utente. In questa sezione vengono illustrati i concetti relativi alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie e alla selezione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Vengono descritte le gerarchie dei progetti e il concetto generale di gerarchie.

- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Viene descritto come l'ambiente di sviluppo integrato (IDE) gestisce le informazioni sugli oggetti attualmente attivi dell'utente e consente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ai vspackage di tenere traccia della valuta.

- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)

 Illustra il modello per determinare lo stato attivo del contesto di selezione dell'utente in una finestra.

- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)

 Viene illustrato come le funzionalità disponibili in si basano sul contesto di selezione corrente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'utente e sul contesto IDE complessivo.

## <a name="related-sections"></a>Sezioni correlate
- [Project tipi di dati](../../extensibility/internals/project-types-architecture.md)

 Fornisce informazioni tecniche dettagliate sui tipi di progetto.
