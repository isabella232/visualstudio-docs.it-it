---
title: Le gerarchie e selezione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 741d61f4f3a62638e56aabb1f62f97aac4519d0c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596581"
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