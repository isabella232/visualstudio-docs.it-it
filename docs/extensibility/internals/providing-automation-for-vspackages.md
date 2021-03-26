---
title: Fornire l'automazione per i pacchetti VSPackage | Microsoft Docs
description: Informazioni su come fornire l'automazione per i pacchetti Vspackage implementando oggetti specifici del pacchetto VSPackage e implementando oggetti di automazione standard.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f9a19b5e0e543052dad492ab319595c8ef76dfe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060952"
---
# <a name="providing-automation-for-vspackages"></a>Automazione per i pacchetti VSPackage
Esistono due modi principali per fornire l'automazione per i pacchetti VSPackage: implementando oggetti specifici del pacchetto VSPackage e implementando oggetti di automazione standard. In genere, vengono usati insieme per estendere il modello di automazione dell'ambiente.

## <a name="vspackage-specific-objects"></a>Oggetti VSPackage-Specific
 Per alcune posizioni all'interno del modello di automazione è necessario fornire oggetti di automazione che siano univoci per il pacchetto VSPackage. I nuovi progetti, ad esempio, richiedono oggetti distinti forniti solo dal pacchetto VSPackage. I nomi di questi oggetti vengono immessi nel registro di sistema e ottenuti tramite chiamate all' `DTE` oggetto ambiente.

 È possibile ottenere oggetti specifici del pacchetto VSPackage anche quando un consumer di automazione utilizza l'oggetto fornito tramite la proprietà Object di un oggetto standard. Ad esempio, l' `Window` oggetto standard dispone di una `Object` proprietà, nota comunemente come `Windows.Object` Proprietà. Quando gli utenti chiamano il in `Window.Object` una finestra implementata nel pacchetto VSPackage, viene passato un oggetto di automazione specifico della propria progettazione.

#### <a name="projects"></a>Progetti
 I pacchetti VSPackage possono estendere il modello di automazione per i nuovi tipi di progetto tramite oggetti specifici del pacchetto VSPackage. Lo scopo principale di fornire nuovi oggetti di automazione per il pacchetto VSPackage consiste nel differenziare gli oggetti di progetto univoci da un <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> <xref:VSLangProj80.VSProject2> oggetto o. Questa differenziazione è utile quando si desidera fornire un modo per uniformare o iterare il tipo di progetto oltre ad altri tipi di progetto, se vengono visualizzati side-by-side in una soluzione. Per ulteriori informazioni, vedere [esposizione di oggetti progetto](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Eventi
 L'architettura dell'evento dell'ambiente offre un'altra posizione in cui è possibile aggiungere oggetti specifici del pacchetto VSPackage. Se ad esempio si creano oggetti evento univoci, è possibile estendere il modello di eventi dell'ambiente per i progetti. Potrebbe essere necessario fornire eventi personalizzati quando un nuovo elemento viene aggiunto al tipo di progetto. Per ulteriori informazioni, vedere [esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Oggetti finestra
 Windows può restituire all'ambiente un oggetto di automazione specifico di VSPackage quando viene chiamato. Si implementa un oggetto derivato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> o che consente di `IDispatch` riportare le proprietà estendendo l'oggetto finestra in cui si trova il sito. Ad esempio, è possibile usare questo approccio per fornire l'automazione per un controllo presente in una cornice della finestra. La semantica di questo oggetto e di tutti gli altri oggetti che potrebbero estenderne è la progettazione. Per altre informazioni, vedere [procedura: fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Pagine opzioni del menu strumenti
 È possibile creare pagine per estendere gli strumenti, il modello di automazione opzioni tramite l'implementazione di pagine e l'aggiunta di informazioni al registro di sistema per creare opzioni personalizzate. Le pagine possono quindi essere chiamate tramite il modello a oggetti dell'ambiente come qualsiasi altra pagina di opzioni. Se la progettazione della funzionalità da aggiungere all'ambiente tramite VSPackage richiede le pagine opzioni, è necessario aggiungere anche il supporto per l'automazione. Per ulteriori informazioni, vedere [supporto di automazione per le pagine opzioni](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Oggetti di automazione standard
 Per estendere l'automazione per i progetti, è anche possibile implementare oggetti di automazione standard (derivati da `IDispatch` ) che si trovano accanto agli altri oggetti di progetto e implementano metodi e proprietà standard. Esempi di oggetti standard includono gli oggetti progetto inseriti nella gerarchia della soluzione, ad esempio `Projects` ,, `Project` `ProjectItem` e `ProjectItems` . Ogni nuovo tipo di progetto deve implementare questi oggetti, e possibilmente altri, a seconda della semantica del progetto.

 In un certo senso, questi oggetti forniscono il vantaggio opposto degli oggetti di progetto specifici di VSPackage. Gli oggetti di automazione standard consentono di usare il progetto in modo generalizzato, come qualsiasi altro progetto che supporta gli stessi oggetti. Pertanto, un componente aggiuntivo scritto su generale `Project` e `ProjectItem` sugli oggetti può funzionare in base a progetti di qualsiasi tipo. Per ulteriori informazioni, vedere Creazione di [modelli di progetto](../../extensibility/internals/project-modeling.md).
