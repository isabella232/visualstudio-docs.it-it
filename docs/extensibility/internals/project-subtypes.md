---
title: Sottotipi di progetto | Microsoft Docs
description: Informazioni su come i sottotipi di progetto consentono di personalizzare il comportamento dei sistemi di progetto Visual Studio. I pacchetti VSPackage implementano sottotipi di progetto usando l'aggregazione COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd0f959d300fdc797d9e42d581a163b8b0892591
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903580"
---
# <a name="project-subtypes"></a>Sottotipi di progetto
I sottotipi di progetto consentono di personalizzare o modificare il comportamento dei sistemi di progetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Le personalizzazioni includono il salvataggio di dati aggiuntivi  nel file di progetto, l'aggiunta o il filtro di elementi nella finestra di dialogo Aggiungi nuovo elemento, il controllo della modalità di debug e distribuzione degli assembly e l'estensione della finestra di dialogo Pagine delle proprietà **del** progetto. I pacchetti VSPackage implementano sottotipi di progetto usando l'aggregazione COM.

> [!NOTE]
> Il Visual C++ di progetto non supporta i sottotipi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa sottotipi di progetto per implementare progetti SQL Server e Smart Device.

## <a name="in-this-section"></a>Contenuto della sezione

- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)

  Descrive il concetto di sottotipi di progetto.

- [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Descrive la sequenza di inizializzazione del sottotipo di progetto a livello di codice in base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] all'ambiente.

- [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Vengono fornite descrizioni dettagliate delle funzionalità e dei metodi più spesso estesi tramite sottotipi di progetto.

- [Salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Viene descritto come rendere persistenti i dati in un file di progetto e come utilizzare per gestire i dati nel file di progetto nei livelli di aggregazione <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> del sottotipo di progetto.

- [Interfaccia utente delle proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)

  Viene descritto come i sottotipi di progetto possono modificare la finestra di **dialogo Pagine delle proprietà** del progetto.

- [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Fornisce informazioni su come i sottotipi di progetto possono usare gli extender di automazione per estendere il modello a oggetti di automazione.

- [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Viene descritto come aggiungere elementi alla finestra **di dialogo Aggiungi** nuovo elemento .

- [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)

  Spiega in che modo un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo nel file di progetto usando Managed Package Framework (MPF).

- [Gestione della distribuzione specializzata](../../extensibility/internals/handling-specialized-deployment.md)

  Viene illustrato in che modo i sottotipi di progetto possono fornire un comportamento di distribuzione specializzato implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> l'interfaccia .

- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)

  Viene descritta l'aggiunta e la rimozione di pagine delle proprietà in Progettazione progetti.

## <a name="related-sections"></a>Sezioni correlate

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

  Vengono forniti collegamenti ad argomenti che descrivono in dettaglio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i progetti.
