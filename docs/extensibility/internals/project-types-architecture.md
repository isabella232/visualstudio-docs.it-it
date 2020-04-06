---
title: Architettura dei tipi di progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706313"
---
# <a name="project-types-architecture"></a>Architettura dei tipi di progetto
In questa sezione sono contenute informazioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dettagliate sull'architettura dei tipi di progetto in .

## <a name="in-this-section"></a>Contenuto della sezione
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)

 Elenca i servizi che un tipo di progetto può utilizzare e le interfacce che deve implementare.

- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)

 Vengono descritte le interfacce che i tipi di progetto devono implementare e, facoltativamente, possono implementare per fornire funzionalità aggiuntive.

- [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)

 Consente di decidere quando è necessario creare un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tipo di progetto e quando è possibile utilizzare un'altra funzionalità di estendibilità, ad esempio VSPackage ed editor per raggiungere lo stesso obiettivo.

- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)

 Viene descritto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come utilizzare le gerarchie e il contesto di selezione per fornire un'esperienza utente coerente e semplificata.

## <a name="related-sections"></a>Sezioni correlate
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Viene illustrato come i sottotipi di progetto consentono [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]di personalizzare il comportamento dei sistemi di progetto di e .

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Fornisce una panoramica dei progetti come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] blocchi predefiniti di base dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
