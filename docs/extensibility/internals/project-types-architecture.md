---
title: Architettura di tipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318890"
---
# <a name="project-types-architecture"></a>Architettura dei tipi di progetto
In questa sezione contiene informazioni dettagliate sull'architettura dei tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>In questa sezione
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)

 Elenca i servizi che può utilizzare un tipo di progetto e le interfacce che deve implementare.

- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)

 Descrive le interfacce di tipi di progetto devono implementare sia possono implementare facoltativamente per fornire funzionalità aggiuntive.

- [Quando creare tipi di progetto](../../extensibility/internals/when-to-create-project-types.md)

 Consente di decidere quando è necessario creare un progetto di tipo e quando è possibile usare un altro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funzionalità di estendibilità, ad esempio editor e i pacchetti VSPackage per ottenere lo stesso scopo.

- [Gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md)

 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Usa le gerarchie e il contesto di selezione per offrire un'esperienza utente coerente e semplificata.

## <a name="related-sections"></a>Sezioni correlate
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)

 Viene spiegato come sottotipi di progetto consentono di personalizzare il comportamento dei sistemi di progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Viene fornita una panoramica di progetti come blocchi predefiniti di base del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.