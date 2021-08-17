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
ms.openlocfilehash: 77ca0dbfd8476aae3b7dc8a12a0a449eb074da4480aa2f2546bc12c7282690ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376183"
---
# <a name="hierarchies-and-selection"></a>Gerarchie e selezione
Quando si personalizza , è necessario comprendere in che modo gestisce le gerarchie, ad esempio i progetti, e come usa il contesto di selezione per determinare ciò che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene visualizzato all'utente. In questa sezione vengono illustrati i concetti relativi alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie e alla selezione.

## <a name="in-this-section"></a>Contenuto della sezione
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Vengono descritte le gerarchie di progetto e il concetto generale di gerarchie.

- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Descrive il modo in cui l'ambiente di sviluppo integrato (IDE) gestisce le informazioni sugli oggetti attualmente attivi dell'utente e consente ai pacchetti VSPackage di tenere traccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della valuta.

- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)

 Viene illustrato il modello per determinare lo stato attivo del contesto di selezione dell'utente in una finestra.

- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)

 Viene illustrato in che modo la funzionalità disponibile in si basa sul contesto di selezione corrente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'utente e sul contesto IDE complessivo.

## <a name="related-sections"></a>Sezioni correlate
- [Project tipi di dati](../../extensibility/internals/project-types-architecture.md)

 Fornisce informazioni tecniche dettagliate sui tipi di progetto.
