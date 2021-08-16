---
title: Strumenti personalizzati | Microsoft Docs
description: Informazioni su come creare strumenti personalizzati in Visual Studio che associano uno strumento a un elemento in un progetto ed eseguono tale strumento ogni volta che il file viene salvato.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e414b8a27ee64832d13d6f4614e53131bb9bae4dd01bee63715c9c28edf5493a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359637"
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti* personalizzati consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Alcuni strumenti personalizzati, talvolta definiti generatori a *file* singolo, vengono spesso usati per implementare convertitori che generano codice dai dati e viceversa. Ad esempio, i generatori a file singolo creano e il codice [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sorgente dei *file con* estensione settings *e resx.* Il codice sorgente generato fornisce l'accesso fortemente tipizzato ai dati nei file con estensione *settings* *e resx.* I [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipi di progetto e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] supportano strumenti personalizzati. I [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipi di progetto non lo supportano. Anche i tipi di progetto personalizzati possono supportare strumenti personalizzati.

 Gli strumenti personalizzati sono componenti registrati che implementano `IVsSingleFileGenerator` l'interfaccia .

 Gli strumenti personalizzati sono associati a un `ProjectItem` oggetto interfaccia e sono simili a finestre di progettazione ed editor. Uno strumento personalizzato accetta il file rappresentato da come input e scrive un nuovo file il `ProjectItem` cui nome file viene fornito dal metodo `DefaultExtension` .

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementare generatori a file singolo](../../extensibility/internals/implementing-single-file-generators.md)

 Viene descritto come utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> l'interfaccia per implementare uno strumento personalizzato.

- [Registrare generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)

 Fornisce descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.

- [Esporre i tipi alle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Viene illustrato in che modo i sistemi di progetto forniscono il supporto per le finestre di progettazione visiva per accedere alle classi e ai tipi generati tramite file eseguibili portabili temporanei (PE).

- [Rendere persistente la proprietà di un elemento di progetto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Illustra come rendere persistente una proprietà dell'elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.

## <a name="reference"></a>Riferimento
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Fornisce informazioni dettagliate su , che trasforma un singolo file di input in un singolo file di output che può essere compilato <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> o aggiunto a un progetto.

 <xref:EnvDTE.ProjectItem> Viene illustrata `ProjectItem` l'interfaccia , che rappresenta un elemento in un progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Fornisce informazioni dettagliate `DefaultExtension` sul metodo , che recupera l'estensione di file fornita al nome del file di output.

## <a name="related-sections"></a>Sezioni correlate
- [Estendere i progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
