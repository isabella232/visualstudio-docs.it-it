---
title: Automazione per i pacchetti VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b72e1493e8ab00f3aa98f3a9bd8e1e1dd30201e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909069"
---
# <a name="providing-automation-for-vspackages"></a>Automazione per i pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esistono due modi per fornire l'automazione per i pacchetti VSPackage: implementando oggetti specifici di un pacchetto VSPackage e mediante l'implementazione di oggetti di automazione standard. In genere, questi vengono usati insieme per estendere il modello di automazione dell'ambiente.  
  
## <a name="vspackage-specific-objects"></a>Oggetti specifici di un pacchetto VSPackage  
 Determinate posizioni all'interno del modello di automazione richiedono di fornire oggetti di automazione che sono univoci per il pacchetto VSPackage. Ad esempio, i nuovi progetti richiedono oggetti distinti che fornisce solo il pacchetto VSPackage. I nomi di questi oggetti vengono immessi nel Registro di sistema e ottenuti tramite chiamate all'ambiente `DTE` oggetto.  
  
 Oggetti specifici di un pacchetto VSPackage possono anche essere ottenuti quando un consumer di automazione utilizza l'oggetto fornito tramite la proprietà dell'oggetto di un oggetto standard. Ad esempio, lo standard `Window` oggetto ha un `Object` proprietà, comunemente noti come il `Windows.Object` proprietà. Quando i consumer chiamano il `Window.Object` in una finestra del implementato nel pacchetto VSPackage passare nuovamente un oggetto di automazione specifico di propria progettazione.  
  
#### <a name="projects"></a>Progetti  
 I VSPackage possono estendere il modello di automazione per i nuovi tipi di progetto tramite i propri oggetti specifico del VSPackage. Lo scopo principale di fornire i nuovi oggetti di automazione per il pacchetto VSPackage è per differenziare il progetto univoco oggetti da un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o un <xref:VSLangProj80.VSProject2> oggetto. Questa distinzione è utile quando si desidera fornire un modo per l'accesso single out o eseguire l'iterazione del tipo di progetto a parte di altri tipi di progetto deve appaiono side-by-side in una soluzione. Per altre informazioni, vedere [esposizione di oggetti del progetto](../../extensibility/internals/exposing-project-objects.md).  
  
#### <a name="events"></a>Eventi  
 L'architettura di evento dell'ambiente offre un altro posto per l'utente al quale accodare oggetti personalizzati specifico del VSPackage. Ad esempio, tramite la creazione di oggetti evento univoco, è possibile estendere il modello di evento dell'ambiente per i progetti. È possibile fornire i propri eventi quando viene aggiunto un nuovo elemento per il proprio tipo di progetto. Per altre informazioni, vedere [esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).  
  
#### <a name="window-objects"></a>Oggetti finestra  
 Windows può passare nuovamente un oggetto di automazione specifico del VSPackage nell'ambiente quando viene chiamato. Implementare un oggetto derivato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> o `IDispatch` che passa indietro di proprietà, estendendo l'oggetto finestra in cui viene individuato. Ad esempio, è possibile usare questo approccio per fornire l'automazione per un controllo posizionato nella cornice della finestra. La semantica di questo oggetto e qualsiasi altro oggetto che è possibile estendere è quelle in uso per la progettazione. Per altre informazioni, vedere [Procedura: Fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).  
  
#### <a name="options-pages-on-the-tools-menu"></a>Pagine Opzioni del menu Strumenti  
 È possibile creare pagine per estendere gli strumenti, il modello di automazione opzioni tramite l'implementazione delle pagine e l'aggiunta di informazioni nel Registro di sistema per creare le proprie opzioni. Le pagine possono quindi essere chiamate tramite il modello a oggetti ambiente, ad esempio tutte le altre pagine di opzioni. Se la progettazione della funzionalità di cui che si sta aggiungendo all'ambiente tramite pacchetti VSPackage richiede che le pagine di opzioni, è necessario aggiungere anche il supporto di automazione. Per altre informazioni, vedere [supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md).  
  
## <a name="standard-automation-objects"></a>Oggetti di automazione standard  
 Per estendere l'automazione per i progetti, si implementano anche gli oggetti di automazione standard (derivato da `IDispatch`) che in evidenza accanto ad altri oggetti di progetto e implementare le proprietà e metodi standard. Esempi di oggetti standard includono gli oggetti di progetto che vengono inseriti nella gerarchia della soluzione, ad esempio `Projects`, `Project`, `ProjectItem`, e `ProjectItems`. Ogni nuovo tipo di progetto deve implementare questi oggetti (e possibilmente altri registri in base alla semantica del progetto).  
  
 In un certo senso, questi oggetti offrono il vantaggio degli oggetti di progetto specifico del VSPackage opposto. Gli oggetti di automazione standard consentono il progetto da usare in modo generalizzato come qualsiasi altro progetto che supportano gli stessi oggetti. Di conseguenza, un componente aggiuntivo che viene scritto su general `Project` e `ProjectItem` oggetti possono funzionare per i progetti di qualsiasi tipo. Per altre informazioni, vedere [progetto di modellazione](../../extensibility/internals/project-modeling.md).
