---
title: Fornire automazione per vspackage | Microsoft Docs
description: Informazioni su come fornire automazione per i pacchetti VSPackage implementando oggetti specifici di VSPackage e implementando oggetti di automazione standard.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b7432ed87b5ff633f9f295f9805eeafb9a0d50b7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636075"
---
# <a name="providing-automation-for-vspackages"></a>Automazione per i pacchetti VSPackage
Esistono due modi principali per fornire automazione per i pacchetti VSPackage: implementando oggetti specifici di VSPackage e implementando oggetti di automazione standard. In genere, vengono usati insieme per estendere il modello di automazione dell'ambiente.

## <a name="vspackage-specific-objects"></a>VSPackage-Specific oggetti
 Alcune posizioni all'interno del modello di automazione richiedono di fornire oggetti di automazione univoci per il pacchetto VSPackage. Ad esempio, i nuovi progetti richiedono oggetti distinti forniti solo dal pacchetto VSPackage. I nomi di questi oggetti vengono immessi nel Registro di sistema e ottenuti tramite chiamate all'oggetto `DTE` ambiente.

 Gli oggetti specifici di VSPackage possono essere ottenuti anche quando un consumer di automazione usa l'oggetto fornito tramite la proprietà Object di un oggetto standard. Ad esempio, l'oggetto standard `Window` ha una proprietà , nota `Object` comunemente come proprietà `Windows.Object` . Quando i consumer chiamano `Window.Object` su una finestra implementata nel pacchetto VSPackage, si passa di nuovo un oggetto di automazione specifico della propria progettazione.

#### <a name="projects"></a>Progetti
 I pacchetti VSPackage possono estendere il modello di automazione per i nuovi tipi di progetto tramite i propri oggetti specifici di VSPackage. Lo scopo principale di fornire nuovi oggetti di automazione per il pacchetto VSPackage è distinguere gli oggetti di progetto univoci da un oggetto <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> o <xref:VSLangProj80.VSProject2> . Questa differenziazione è utile quando si vuole fornire un modo per specificare o scorrere il tipo di progetto oltre ad altri tipi di progetto, nel caso in cui vengano visualizzati side-by-side in una soluzione. Per altre informazioni, vedere [Esposizione di Project oggetti](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Eventi
 L'architettura degli eventi dell'ambiente offre un'altra posizione in cui aggiungere oggetti specifici di VSPackage. Ad esempio, creando oggetti evento univoci, è possibile estendere il modello di eventi dell'ambiente per i progetti. È possibile fornire eventi personalizzati quando un nuovo elemento viene aggiunto al proprio tipo di progetto. Per altre informazioni, vedere [Esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Oggetti finestra
 Windows possibile passare nuovamente un oggetto di automazione specifico di VSPackage all'ambiente quando viene chiamato. Si implementa un oggetto derivato da o che trasla le proprietà, estendendo l'oggetto finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> in cui si `IDispatch` trova. Ad esempio, è possibile usare questo approccio per fornire l'automazione per un controllo in una cornice di finestra. La semantica di questo oggetto e di qualsiasi altro oggetto che potrebbe estendersi è da progettare. Per altre informazioni, vedere [Procedura: Fornire automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Pagine delle opzioni del menu Strumenti
 È possibile creare pagine per estendere il modello di automazione Strumenti, Opzioni tramite l'implementazione di pagine e l'aggiunta di informazioni al Registro di sistema per creare opzioni personalizzate. Le pagine possono quindi essere chiamate tramite il modello a oggetti dell'ambiente come qualsiasi altra pagina di opzioni. Se la progettazione della funzionalità da aggiungere all'ambiente tramite VSPackage richiede pagine di opzioni, è necessario aggiungere anche il supporto per l'automazione. Per altre informazioni, vedere [Supporto di Automazione per le pagine delle opzioni](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Oggetti di automazione standard
 Per estendere l'automazione per i progetti, si implementano anche oggetti di automazione standard (derivati da ) che si estendono accanto agli altri oggetti di progetto e implementano metodi `IDispatch` e proprietà standard. Esempi di oggetti standard includono gli oggetti di progetto inseriti nella gerarchia della soluzione, ad esempio `Projects` `Project` , , e `ProjectItem` `ProjectItems` . Ogni nuovo tipo di progetto deve implementare questi oggetti (e possibilmente altri oggetti a seconda della semantica del progetto).

 In un certo senso, questi oggetti offrono il vantaggio opposto degli oggetti di progetto specifici di VSPackage. Gli oggetti di automazione standard consentono di usare il progetto in modo generalizzato come qualsiasi altro progetto che supporti gli stessi oggetti. Di conseguenza, un componente aggiuntivo scritto su oggetti `Project` generali e può funzionare su progetti di qualsiasi `ProjectItem` tipo. Per altre informazioni, vedere [Project Modeling](../../extensibility/internals/project-modeling.md).
