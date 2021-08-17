---
title: Project Architettura dei tipi | Microsoft Docs
description: Questo articolo include collegamenti ad articoli che contengono informazioni dettagliate sull'architettura dei tipi di progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6d42bda91e9714b8deff4822e2e41c2af1af8dc4d2ef96274727d8b5f7f35ff5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401380"
---
# <a name="project-types-architecture"></a>Architettura dei tipi di progetto
Questa sezione contiene informazioni dettagliate sull'architettura dei tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)

 Elenca i servizi che un tipo di progetto può utilizzare e le interfacce che deve implementare.

- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)

 Descrive le interfacce che i tipi di progetto devono entrambi implementare e, facoltativamente, possono implementare per fornire funzionalità aggiuntive.

- [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)

 Consente di decidere quando è necessario creare un tipo di progetto e quando è possibile usare un'altra funzionalità di estendibilità, ad esempio vspackage ed editor, per raggiungere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lo stesso obiettivo.

- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)

 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzare le gerarchie e il contesto di selezione per offrire un'esperienza utente coerente e semplificata.

## <a name="related-sections"></a>Sezioni correlate
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Viene illustrato in che modo i sottotipi di progetto consentono di personalizzare il comportamento dei sistemi di progetto di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene fornita una panoramica dei progetti come blocchi predefiniti di base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione di codice.
