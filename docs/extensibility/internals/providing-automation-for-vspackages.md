---
title: Fornire l'automazione per i pacchetti VSPackage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705954"
---
# <a name="providing-automation-for-vspackages"></a>Automazione per i pacchetti VSPackage
Esistono due modi principali per fornire l'automazione per i pacchetti VSPackage: implementando gli oggetti specifici di VSPackage e implementando gli oggetti di automazione standard. In genere, questi vengono utilizzati insieme per estendere il modello di automazione dell'ambiente.

## <a name="vspackage-specific-objects"></a>Oggetti specifici di VSPackage
 Alcune posizioni all'interno del modello di automazione richiedono di fornire oggetti di automazione univoci per il pacchetto VSPackage.Certain places within the automation model require you to provide automation objects that are unique to your VSPackage. Ad esempio, nuovi progetti richiedono oggetti distinti che fornisce solo il pacchetto VSPackage.For instance, new projects require distinct objects that only your VSPackage provides. I nomi di questi oggetti vengono immessi nel `DTE` Registro di sistema e ottenuti tramite chiamate all'oggetto ambiente.

 Gli oggetti specifici di VSPackage possono essere ottenuti anche quando un consumer di automazione utilizza l'oggetto fornito tramite il Object proprietà di un oggetto standard. Ad esempio, `Window` l'oggetto `Object` standard ha una `Windows.Object` proprietà, nota comunemente come proprietà. Quando i `Window.Object` consumer chiamano il su una finestra implementata nel pacchetto VSPackage, si passa un oggetto di automazione specifico del proprio design.

#### <a name="projects"></a>Progetti
 VSPackage possono estendere il modello di automazione per i nuovi tipi di progetto tramite i propri oggetti specifici di VSPackage.VSPackages can extend the automation model for new project types through their own VSPackage-specific objects. Lo scopo principale di fornire nuovi oggetti di automazione per <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> il <xref:VSLangProj80.VSProject2> pacchetto VSPackage consiste nel differenziare gli oggetti di progetto univoci da un oggetto o un oggetto. Questa differenziazione è utile quando si desidera fornire un modo per individuare o iterare il tipo di progetto oltre ad altri tipi di progetto, devono essere visualizzati side-by-side in una soluzione. Per ulteriori informazioni, vedere [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Events
 L'architettura degli eventi dell'ambiente offre un'altra posizione per aggiungere i propri oggetti specifici di VSPackage.The event architecture of the environment offers another place for you to append your own VSPackage-specific objects. Ad esempio, creando oggetti evento univoci, è possibile estendere il modello di evento dell'ambiente per i progetti. È possibile fornire eventi personalizzati quando un nuovo elemento viene aggiunto al proprio tipo di progetto. Per ulteriori informazioni, vedere [Esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Oggetti finestra
 Windows può passare nuovamente un oggetto di automazione specifico di VSPackage all'ambiente quando viene chiamato. Implementare un oggetto derivato <xref:EnvDTE.IExtensibleObject> `IDispatch` da <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>o che esegue le proprietà, estendendo l'oggetto finestra in cui si trova. Ad esempio, è possibile utilizzare questo approccio per fornire l'automazione per un controllo che si trova in una cornice della finestra. La semantica di questo oggetto e di qualsiasi altro oggetto che potrebbe estendere è tua per la progettazione. Per ulteriori informazioni, vedere [Procedura: fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Pagine Opzioni del menu Strumenti
 È possibile creare pagine per estendere il modello di automazione Strumenti, Opzioni tramite l'implementazione di pagine e l'aggiunta di informazioni al Registro di sistema per creare opzioni personalizzate. Le pagine possono quindi essere chiamate tramite il modello a oggetti dell'ambiente come qualsiasi altra pagina di opzioni. Se la progettazione della funzionalità che si sta aggiungendo all'ambiente tramite VSPackage richiede pagine di opzioni, è necessario aggiungere anche il supporto di automazione. Per ulteriori informazioni, vedere [Supporto dell'automazione per](../../extensibility/internals/automation-support-for-options-pages.md)le pagine delle opzioni .

## <a name="standard-automation-objects"></a>Oggetti di automazione standard
 Per estendere l'automazione per i progetti, `IDispatch`si implementano anche oggetti di automazione standard (derivati da ) che si trovano accanto agli altri oggetti di progetto e implementano metodi e proprietà standard. Esempi di oggetti standard includono gli oggetti di progetto `Projects` `Project`che `ProjectItem`vengono `ProjectItems`inseriti nella gerarchia della soluzione, ad esempio , , e . Ogni nuovo tipo di progetto deve implementare questi oggetti (ed eventualmente altri a seconda della semantica del progetto).

 In un certo senso, questi oggetti forniscono il vantaggio opposto degli oggetti di progetto specifici di VSPackage. Gli oggetti di automazione standard consentono al progetto di essere utilizzato in modo generalizzato come qualsiasi altro progetto che supporta gli stessi oggetti. Pertanto, un componente aggiuntivo che `Project` `ProjectItem` viene scritto in generale e gli oggetti possono funzionare su progetti di qualsiasi tipo. Per ulteriori informazioni, vedere [Modellazione di progetto](../../extensibility/internals/project-modeling.md).
