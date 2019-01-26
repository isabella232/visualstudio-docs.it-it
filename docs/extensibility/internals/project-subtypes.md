---
title: Sottotipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2e5151131efdab36a3c9e5cf646b1ca9bf94b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922717"
---
# <a name="project-subtypes"></a>Sottotipi di progetto
Sottotipi di progetto consentono di personalizzare o specificare il comportamento dei sistemi di progetto di una versione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Le personalizzazioni includono il salvataggio dei dati aggiuntivi nel file di progetto, aggiungendo o filtrando gli elementi di **Aggiungi nuovo elemento** della finestra di dialogo controllo come gli assembly vengono eseguito il debug e distribuiti ed estendendo il progetto **proprietà Pagine** nella finestra di dialogo. I pacchetti VSPackage implementare sottotipi di progetto tramite aggregazione COM.  
  
> [!NOTE]
>  Il sistema di progetto Visual C++ non supporta sottotipi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sottotipi di progetto stesso utilizzato per implementare progetti Smart Device e SQL Server.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Progettazione di sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)  
 Descrive il concetto di sottotipi di progetto.  
  
 [Sequenza di inizializzazione dei sottotipi di progetto](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Viene descritta la sequenza di inizializzazione sottotipo di progetto a livello di codice da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.  
  
 [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Vengono fornite descrizioni dettagliate delle funzionalità e dei metodi più di frequente estesi usando sottotipi di progetto.  
  
 [Salvataggio permanente dei dati nel file di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Viene descritto come rendere persistenti i dati in un file di progetto e come usare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per mantenere i dati nel file di progetto tra i livelli di aggregazione sottotipo di progetto.  
  
 [Interfaccia utente delle proprietà del progetto](../../extensibility/internals/project-property-user-interface.md)  
 Viene descritto come sottotipi di progetto possono modificare il progetto **pagine delle proprietà** nella finestra di dialogo.  
  
 [Estensione del modello a oggetti del progetto di base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Fornisce informazioni su come sottotipi di progetto usare estensioni di automazione per estendere il modello oggetto di automazione.  
  
 [Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Viene descritto come aggiungere elementi per il **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 [Salvataggio di dati nei file di progetto](../../extensibility/saving-data-in-project-files.md)  
 Viene illustrato come un sottotipo di progetto può salvare e recuperare dati specifici del sottotipo del file di progetto usando il Framework di pacchetto gestito (MPF).  
  
 [Gestione della distribuzione specializzata](../../extensibility/internals/handling-specialized-deployment.md)  
 Viene spiegato come sottotipi di progetto possono fornire il comportamento della distribuzione specializzata implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia.  
  
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)  
 Descrive l'aggiunta e rimozione di pagine delle proprietà in Progettazione progetti.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono forniti collegamenti ad argomenti che descrivono dettagliatamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti.