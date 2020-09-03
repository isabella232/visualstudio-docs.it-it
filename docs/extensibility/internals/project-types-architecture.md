---
title: Architettura di tipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706313"
---
# <a name="project-types-architecture"></a>Architettura dei tipi di progetto
In questa sezione vengono fornite informazioni dettagliate sull'architettura dei tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)

 Elenca i servizi che possono essere utilizzati da un tipo di progetto e le interfacce che deve implementare.

- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)

 Descrive i tipi di progetto di interfacce che devono implementare ed eventualmente implementare per fornire funzionalità aggiuntive.

- [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)

 Consente di decidere quando è necessario creare un tipo di progetto e quando è possibile utilizzare un'altra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità di estendibilità, ad esempio VSPackage ed editor, per ottenere lo stesso obiettivo.

- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)

 Viene descritto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in che modo utilizza gerarchie e contesto di selezione per offrire un'esperienza utente coerente e semplificata.

## <a name="related-sections"></a>Sezioni correlate
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Viene illustrato come i sottotipi di progetto consentono di personalizzare il comportamento dei sistemi del progetto di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene fornita una panoramica dei progetti come blocchi predefiniti di base dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE). Sono disponibili collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
