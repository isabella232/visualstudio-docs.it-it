---
title: Strumenti personalizzati | Microsoft Docs
description: Informazioni su come creare strumenti personalizzati in Visual Studio che associano uno strumento a un elemento in un progetto e lo eseguono ogni volta che il file viene salvato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d714822605178382ec2ef3574db617f7986cf888
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091045"
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti personalizzati* consentono di associare uno strumento a un elemento in un progetto e di eseguire lo strumento ogni volta che il file viene salvato. Alcuni strumenti personalizzati, detti anche *generatori di file singoli*, vengono spesso usati per implementare i traduttori che generano codice dai dati e viceversa. Ad esempio, i generatori di file singoli creano [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] il codice sorgente dai file *. Settings* e *. resx* . Il codice sorgente generato fornisce un accesso fortemente tipizzato ai dati nei file *. Settings* e *. resx* . I [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto e supportano gli strumenti personalizzati [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . i tipi di progetto non lo supportano. I tipi di progetto possono supportare anche strumenti personalizzati.

 Gli strumenti personalizzati sono componenti registrati che implementano l' `IVsSingleFileGenerator` interfaccia.

 Gli strumenti personalizzati sono associati a un `ProjectItem` oggetto interfaccia e sono come finestre di progettazione ed editor. Uno strumento personalizzato accetta il file rappresentato da `ProjectItem` come input e scrive un nuovo file il cui nome file viene fornito dal `DefaultExtension` metodo.

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementare generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)

 Viene descritto come utilizzare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia per implementare uno strumento personalizzato.

- [Registra generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)

 Fornisce le descrizioni per tutte le voci del registro di sistema per uno strumento personalizzato.

- [Esporre i tipi alle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Spiega in che modo i sistemi di progetto forniscono supporto per le finestre di progettazione visiva per accedere a classi e tipi generati tramite file eseguibili portabili (PE) temporanei.

- [Rende permanente la proprietà di un elemento di progetto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Viene illustrato come salvare in modo permanente una proprietà di un elemento del progetto, ad esempio l'autore di un file di origine, nel file di progetto.

## <a name="reference"></a>Riferimento
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Fornisce informazioni dettagliate su <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , che trasforma un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.

 <xref:EnvDTE.ProjectItem> Viene illustrata l' `ProjectItem` interfaccia, che rappresenta un elemento in un progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Fornisce informazioni dettagliate sul `DefaultExtension` metodo, che recupera l'estensione del nome file assegnata al nome del file di output.

## <a name="related-sections"></a>Sezioni correlate
- [Estendi progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
