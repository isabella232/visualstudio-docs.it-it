---
title: Sottotipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c528486db99ddf07b2a2d1e18dcee4fc46e8713b
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426976"
---
# <a name="project-subtypes"></a>Sottotipi di progetto
I sottotipi di progetto consentono di personalizzare o insaporire il comportamento dei sistemi del progetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Le personalizzazioni includono il salvataggio di dati aggiuntivi nel file di progetto, l'aggiunta o il filtro di elementi nella finestra di dialogo **Aggiungi nuovo elemento** , il controllo della modalità di debug e distribuzione degli assembly e l'estensione della finestra di dialogo **pagine delle proprietà** del progetto. I pacchetti VSPackage implementano sottotipi di progetto tramite l'aggregazione COM.

> [!NOTE]
> Il sistema del progetto Visual C++ non supporta sottotipi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] USA sottotipi di progetto per implementare progetti di SQL Server e Smart Device.

## <a name="in-this-section"></a>Contenuto della sezione

- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)

  Viene descritto il concetto di sottotipi di progetto.

- [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  Descrive la sequenza di inizializzazione del sottotipo di progetto programmatico in base all' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.

- [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  Vengono fornite descrizioni dettagliate delle funzionalità e dei metodi estesi con maggiore frequenza utilizzando sottotipi di progetto.

- [Salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  Viene descritto come mantenere i dati in un file di progetto e come utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per gestire i dati nel file di progetto nei livelli di aggregazione del sottotipo di progetto.

- [Interfaccia utente delle proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)

  Viene descritto in che modo i sottotipi di progetto possono modificare la finestra di dialogo **pagine delle proprietà** del progetto.

- [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  Fornisce informazioni sul modo in cui i sottotipi di progetto possono utilizzare le estensioni di automazione per estendere il modello a oggetti di automazione.

- [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  Viene descritto come aggiungere elementi alla finestra di dialogo **Aggiungi nuovo elemento** .

- [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)

  Viene illustrato come un sottotipo di progetto può salvare e recuperare i dati specifici del sottotipo nel file di progetto usando il Framework di pacchetto gestito (MPF).

- [Gestione della distribuzione specializzata](../../extensibility/internals/handling-specialized-deployment.md)

  Spiega in che modo i sottotipi di progetto possono fornire un comportamento di distribuzione specializzato implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia.

- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)

  Viene descritto come aggiungere e rimuovere pagine delle proprietà in Progettazione progetti.

## <a name="related-sections"></a>Sezioni correlate

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

  Fornisce collegamenti ad argomenti che descrivono i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti.
