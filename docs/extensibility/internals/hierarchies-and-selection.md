---
title: Le gerarchie e selezione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d59a5160b5c20a3243426eaf1fda4b72e58e93
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328872"
---
# <a name="hierarchies-and-selection"></a>Le gerarchie e selezione
Quando si personalizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario comprendere come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le gerarchie, ad esempio i progetti e utilizza come contesto di selezione per determinare ciò che viene visualizzato all'utente. In questa sezione illustra i concetti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie e selezione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Descrive il concetto generale di gerarchie e le gerarchie di progetto.

- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Viene descritto come il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) mantiene le informazioni sugli oggetti attualmente attiva dell'utente e consente a pacchetti VSPackage di tenere traccia di tipo valuta.

- [Oggetti di contesto di selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per come è possibile determinare lo stato attivo contesto di selezione dell'utente in una finestra.

- [Commenti e suggerimenti all'utente](../../extensibility/internals/feedback-to-the-user.md)

 Viene illustrato come le funzionalità disponibili nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è basata sul contesto della selezione corrente e il contesto IDE complessiva dell'utente.

## <a name="related-sections"></a>Sezioni correlate
- [Architettura dei tipi di progetto](../../extensibility/internals/project-types-architecture.md)

 Fornisce informazioni tecniche dettagliate sui tipi di progetto.