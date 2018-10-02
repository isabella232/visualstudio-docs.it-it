---
title: Gli strumenti personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72fb6f9f0ceb3b9f2ae04f39b2c37c416acf47b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526300"
---
# <a name="custom-tools"></a>Strumenti personalizzati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [strumenti personalizzati](https://docs.microsoft.com/visualstudio/extensibility/internals/custom-tools).  
  
*Gli strumenti personalizzati* consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che viene salvato il file. Alcuni strumenti personalizzati, anche detta *generatori di file singoli*, vengono spesso usati per implementare i traduttori che generano codice dai dati e viceversa. Ad esempio, creano i generatori di file singolo [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] codice all'esterno di Settings e resx in file di origine. Il codice sorgente generato fornisce accesso fortemente tipizzato ai dati nei file con estensione resx e. Settings. Il [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipi di progetto supportano gli strumenti personalizzati; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] non li supportano tipi di progetto. Tipi di progetto personalizzati possono anche supportare gli strumenti personalizzati.  
  
 Gli strumenti personalizzati verranno registrati i componenti che implementano il `IVsSingleFileGenerator` interfaccia.  
  
 Gli strumenti personalizzati sono associati un `ProjectItem` oggetto di interfaccia e sono simili a editor e finestre di progettazione. Uno strumento personalizzato accetta il file rappresentato da un `ProjectItem` come input e scrive un nuovo file il cui nome viene fornito per il `DefaultExtension` (metodo).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)  
 Viene descritto come utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia da implementare uno strumento personalizzato.  
  
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)  
 Descrive come determinare lo spazio dei nomi corretto in base alla lingua in uso.  
  
 [Registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)  
 Vengono fornite descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.  
  
 [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Viene illustrato come i sistemi di progetto forniscono supporto per finestre di progettazione visiva per classi di accesso generato e i tipi tramite i file temporanei eseguibile portabile (PE).  
  
 [Salvataggio permanente della proprietà di un elemento di progetto](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Viene illustrato come salvare in modo permanente una proprietà di elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Vengono forniti dettagli sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, che trasforma un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.  
  
 <xref:EnvDTE.ProjectItem>  
 Viene illustrato il `ProjectItem` interfaccia che rappresenta un elemento in un progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Vengono forniti dettagli sul `DefaultExtension` metodo, che recupera l'estensione del nome file che viene assegnato al nome del file di output.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Estensione dei progetti](../../extensibility/extending-projects.md)  
 Viene descritto come utilizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetti e soluzioni per organizzare i file di codice e i file di risorse e come implementare il codice sorgente.

