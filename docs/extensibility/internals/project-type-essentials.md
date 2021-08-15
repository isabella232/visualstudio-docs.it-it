---
title: Project Digitare Essentials | Microsoft Docs
description: Informazioni su quando è necessario creare un tipo di progetto e su quando è possibile estendere un tipo di progetto esistente usando sottotipi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 758cc981e1c202f28693d780dbc06089a061d9984b2f7208d5da983c0922d080
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401383"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] include diversi tipi di progetto per i linguaggi, ad [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] esempio o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente anche di creare tipi di progetto personalizzati.

 Se si vogliono solo aggiungere comandi, editor o finestre degli strumenti personalizzati a , è possibile farlo senza creare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)

  Analogamente, se si vuole personalizzare il comportamento dei tipi di progetto e forniti, è possibile farlo usando i sottotipi [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] di progetto. Per altre informazioni, vedere [Project Subtypes](../../extensibility/internals/project-subtypes.md).

  È necessario creare un nuovo tipo di progetto per i progetti basati su un linguaggio diverso da e se si desidera supportare uno o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] più degli elementi [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] seguenti:

- Compilare

- Distribuzione

- Più configurazioni

- Controllo del codice sorgente

- Debug

- Project elementi in Esplora soluzioni

- Finestre **di dialogo Apri** Project o **Project** nuova finestra di dialogo

- Project annidamento

- Per altre informazioni sulle funzionalità dei tipi di progetto, vedere gli argomenti seguenti:

- Project tipi sono oggetti in un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] previsto. Se si usa C# per sviluppare un tipo di progetto, le classi di progetto del framework del pacchetto gestito implementano automaticamente le interfacce necessarie e consentono di ereditare tale implementazione. Per altre informazioni, vedere [Using the Managed Package Framework to Implement a Project Type (C#) .](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Per gli sviluppatori C++, le classi nella libreria HierUtil funzionano in modo simile. Per altre informazioni, vedere [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++) .](/previous-versions/bb166212(v=vs.100))

- Project tipi possono supportare dati diversi da file di codice sorgente tipici compilati in un assembly .exe o .dll assembly. Ad esempio, i progetti di database contengono riferimenti a file di script ed query archiviati su disco e aggiungono comandi a Esplora soluzioni per eseguire script e query su un database, ma i progetti non supportano il comportamento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilazione.  Per altre informazioni, vedere [Apertura e salvataggio Project elementi](../../extensibility/internals/opening-and-saving-project-items.md).

- Un tipo di progetto non deve usare file. Ad esempio, un tipo di progetto potrebbe archiviare tutti i relativi dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre ai tipi di progetto il controllo completo sulla modalità di persistenza dei dati per i progetti e gli elementi del progetto. Per altre informazioni, vedere l'Project [di progettazione dei tipi.](../../extensibility/internals/project-type-design-decisions.md)

- Project tipi di progetto devono fornire una *factory* del progetto, ovvero un oggetto che crea un'istanza del tipo di progetto ogni volta che viene specificato di aprire o creare un progetto basato su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tale tipo di progetto. Per altre informazioni, vedere [Creating Project Instances By Using Project Factoryies](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Project devono fornire modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa i modelli quando gli utenti creano nuovi progetti e aggiungono nuovi elementi ai progetti esistenti. Per altre informazioni, vedere [Adding Project and Project Item Templates](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Project tipi possono supportare più configurazioni, ad esempio Debug e Release. Gli utenti possono modificare le diverse configurazioni di un progetto usando le pagine delle proprietà fornite dall'utente. Per altre informazioni, vedere [Gestione delle opzioni di configurazione.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Vedi anche
- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)