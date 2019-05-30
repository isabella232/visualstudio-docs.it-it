---
title: Gli strumenti personalizzati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9bad62d071fd7c2ef6e0a7c1f5500a5fccb18e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312260"
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti personalizzati* consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che viene salvato il file. Alcuni strumenti personalizzati, anche detta *generatori di file singoli*, vengono spesso usati per implementare i traduttori che generano codice dai dati e viceversa. Ad esempio, creano i generatori di file singolo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] out del codice sorgente il *Settings* e *resx* file. Il codice sorgente generato fornisce accesso fortemente tipizzato ai dati di *Settings* e *resx* file. Il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto supportano gli strumenti personalizzati; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] non li supportano tipi di progetto. Tipi di progetto personalizzati possono anche supportare gli strumenti personalizzati.

 Gli strumenti personalizzati verranno registrati i componenti che implementano il `IVsSingleFileGenerator` interfaccia.

 Gli strumenti personalizzati sono associati un `ProjectItem` oggetto di interfaccia e sono simili a editor e finestre di progettazione. Uno strumento personalizzato accetta il file rappresentato da un `ProjectItem` come input e scrive un nuovo file il cui nome viene fornito per il `DefaultExtension` (metodo).

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementare generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)

 Viene descritto come utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia da implementare uno strumento personalizzato.

- [I generatori di singolo file di registrazione](../../extensibility/internals/registering-single-file-generators.md)

 Vengono fornite descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.

- [Esporre i tipi di finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Viene illustrato come i sistemi di progetto forniscono supporto per finestre di progettazione visiva per classi di accesso generato e i tipi tramite i file temporanei eseguibile portabile (PE).

- [Rendere permanente la proprietà di un elemento del progetto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Viene illustrato come salvare in modo permanente una proprietà di elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.

## <a name="reference"></a>Riferimenti
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Vengono forniti dettagli sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, che trasforma un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.

 <xref:EnvDTE.ProjectItem> Viene illustrato il `ProjectItem` interfaccia che rappresenta un elemento in un progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Vengono forniti dettagli sul `DefaultExtension` metodo, che recupera l'estensione del nome file che viene assegnato al nome del file di output.

## <a name="related-sections"></a>Sezioni correlate
- [Estendere i progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.