---
title: Gli strumenti personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 306173876d0fd7c4d1da76d1b5432ecd5358c425
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500239"
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti personalizzati* consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che viene salvato il file. Alcuni strumenti personalizzati, anche detta *generatori di file singoli*, vengono spesso usati per implementare i traduttori che generano codice dai dati e viceversa. Ad esempio, creano i generatori di file singolo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] out del codice sorgente il *Settings* e *resx* file. Il codice sorgente generato fornisce accesso fortemente tipizzato ai dati di *Settings* e *resx* file. Il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi di progetto supportano gli strumenti personalizzati; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] non li supportano tipi di progetto. Tipi di progetto personalizzati possono anche supportare gli strumenti personalizzati.  
  
 Gli strumenti personalizzati verranno registrati i componenti che implementano il `IVsSingleFileGenerator` interfaccia.  
  
 Gli strumenti personalizzati sono associati un `ProjectItem` oggetto di interfaccia e sono simili a editor e finestre di progettazione. Uno strumento personalizzato accetta il file rappresentato da un `ProjectItem` come input e scrive un nuovo file il cui nome viene fornito per il `DefaultExtension` (metodo).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementare generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)  
 Viene descritto come utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia da implementare uno strumento personalizzato.  
  
 [I generatori di singolo file di registrazione](../../extensibility/internals/registering-single-file-generators.md)  
 Vengono fornite descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.  
  
 [Esporre i tipi di finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Viene illustrato come i sistemi di progetto forniscono supporto per finestre di progettazione visiva per classi di accesso generato e i tipi tramite i file temporanei eseguibile portabile (PE).  
  
 [Rendere permanente la proprietà di un elemento del progetto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Viene illustrato come salvare in modo permanente una proprietà di elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Vengono forniti dettagli sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, che trasforma un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.  
  
 <xref:EnvDTE.ProjectItem>  
 Viene illustrato il `ProjectItem` interfaccia che rappresenta un elemento in un progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Vengono forniti dettagli sul `DefaultExtension` metodo, che recupera l'estensione del nome file che viene assegnato al nome del file di output.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estendere i progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti e soluzioni per organizzare i file di codice e i file di risorse e come implementare il codice sorgente.