---
title: Project Digitare Essentials | Microsoft Docs
description: Informazioni su quando è necessario creare un tipo di progetto e su quando è possibile estendere un tipo di progetto esistente usando i sottotipi di progetto.
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
ms.openlocfilehash: 251b9f9b17e5e20e7a2d039a77155bd2be457388
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117839"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] include diversi tipi di progetto per linguaggi quali [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente anche di creare tipi di progetto personalizzati.

 Se si vogliono solo aggiungere comandi personalizzati, editor o finestre degli strumenti a , è possibile farlo senza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creare un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)

  Analogamente, se si vuole personalizzare il comportamento dei tipi di progetto e forniti, è possibile farlo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usando i sottotipi di progetto. Per altre informazioni, vedere [Sottotipi Project](../../extensibility/internals/project-subtypes.md).

  È necessario creare un nuovo tipo di progetto per i progetti basati su un linguaggio diverso da e se si vuole supportare uno o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] più degli elementi [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] seguenti:

- Compilare

- Distribuzione

- Più configurazioni

- Controllo del codice sorgente

- Debug

- Project elementi in Esplora soluzioni

- Le **finestre di dialogo Apri** Project o **Project** nuovo

- Project annidamento

- Per altre informazioni sulle funzionalità dei tipi di progetto, vedere quanto segue:

- Project tipi sono oggetti in un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] previste. Se si usa C# per sviluppare un tipo di progetto, le classi di progetto managed package framework implementano automaticamente le interfacce necessarie e consentono di ereditare tale implementazione. Per altre informazioni, vedere [Using the Managed Package Framework to Implement a Project Type (C#) .](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Per gli sviluppatori C++, le classi nella libreria HierUtil funzionano in modo simile. Per altre informazioni, vedere [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++) .](/previous-versions/bb166212(v=vs.100))

- Project tipi possono supportare dati diversi da file di codice sorgente tipici compilati in un assembly .exe o .dll assembly. Ad esempio, i progetti di database contengono riferimenti ai file di script e di query archiviati su disco e aggiungono comandi a Esplora soluzioni per eseguire script e query su un database, ma i progetti non supportano il comportamento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilazione.  Per altre informazioni, vedere [Apertura e salvataggio di Project elementi](../../extensibility/internals/opening-and-saving-project-items.md).

- Non è necessario che un tipo di progetto usi i file. Ad esempio, un tipo di progetto può archiviare tutti i dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre ai tipi di progetto il controllo completo sul modo in cui vengono mantenuti i dati per i progetti e gli elementi del progetto. Per altre informazioni, vedere Prendere decisioni [Project di progettazione dei tipi.](../../extensibility/internals/project-type-design-decisions.md)

- Project devono fornire una *factory* di progetto, ovvero un oggetto che crea un'istanza del tipo di progetto ogni volta che viene detto di aprire o creare un progetto basato su tale tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto. Per altre informazioni, vedere [Creazione di istanze Project tramite Project factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Project devono fornire modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa i modelli quando gli utenti creano nuovi progetti e aggiungono nuovi elementi ai progetti esistenti. Per altre informazioni, vedere [Aggiunta di Project e Project di elementi](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Project tipi possono supportare più configurazioni, ad esempio Debug e Release. Gli utenti possono modificare le diverse configurazioni di un progetto usando le pagine delle proprietà specificate. Per altre informazioni, vedere [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Vedi anche
- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)