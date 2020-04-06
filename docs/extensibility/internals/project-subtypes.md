---
title: Sottotipi di progetto Documenti Microsoft
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
ms.openlocfilehash: 71dab4767c806b44cbd1f9638738b4a13d6b2bcb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706402"
---
# <a name="project-subtypes"></a>Sottotipi di progetto
I sottotipi di progetto consentono di personalizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]o insaporire il comportamento dei sistemi di progetto di . Le personalizzazioni includono il salvataggio di dati aggiuntivi nel file di progetto, l'aggiunta o il filtro di elementi nella finestra di dialogo **Aggiungi nuovo elemento,** il controllo della modalità di debug e distribuzione degli assembly e l'estensione della finestra di dialogo **Pagine delle proprietà** del progetto. I package VS implementano i sottotipi di progetto utilizzando l'aggregazione COM.

> [!NOTE]
> Il sistema di progetto di Visual Cè non supporta i sottotipi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza i sottotipi di progetto per implementare i progetti SQL Server e Smart Device.

## <a name="in-this-section"></a>Contenuto della sezione
- [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)

 Descrive il concetto di sottotipi di progetto.

- [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 Viene descritta la sequenza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inizializzazione del sottotipo di progetto a livello di codice in base all'ambiente.

- [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 Vengono fornite descrizioni dettagliate delle funzionalità e dei metodi più frequentemente estesi utilizzando i sottotipi di progetto.

- [Salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 Viene descritto come rendere persistenti i dati <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> in un file di progetto e come utilizzare per gestire i dati nel file di progetto attraverso i livelli di aggregazione dei sottotipi di progetto.

- [Interfaccia utente delle proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)

 Viene descritto come i sottotipi di progetto possono modificare la finestra di dialogo **Pagine delle proprietà** del progetto.

- [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 Vengono fornite informazioni su come i sottotipi di progetto possono utilizzare le estensioni di automazione per estendere il modello a oggetti di automazione.

- [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 Viene descritto come aggiungere elementi alla finestra di dialogo **Aggiungi nuovo elemento.**

- [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)

 Viene illustrato come un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo nel file di progetto utilizzando Managed Package Framework (MPF).

- [Gestione della distribuzione specializzata](../../extensibility/internals/handling-specialized-deployment.md)

 Viene illustrato come i sottotipi di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> possono fornire un comportamento di distribuzione specializzato implementando l'interfaccia.

- [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)

 Vengono descritte l'aggiunta e la rimozione di pagine delle proprietà in Progettazione progetti.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Vengono forniti collegamenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ad argomenti che illustrano in dettaglio i progetti.
