---
title: Informazioni di base sul tipo di progetto | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903557"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] include diversi tipi di progetto per i linguaggi, ad [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] esempio o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente anche di creare tipi di progetto personalizzati.

 Se si vogliono solo aggiungere comandi, editor o finestre degli strumenti personalizzati a , è possibile farlo senza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creare un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)

  Analogamente, se si vuole personalizzare il comportamento dei tipi di progetto e forniti, è possibile farlo usando i sottotipi [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] di progetto. Per altre informazioni, vedere [Sottotipi di progetto.](../../extensibility/internals/project-subtypes.md)

  È necessario creare un nuovo tipo di progetto per i progetti basati su un linguaggio diverso da e se si desidera supportare uno o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] più degli elementi [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] seguenti:

- Compilare

- Distribuzione

- Più configurazioni

- Controllo del codice sorgente

- Debug

- Elementi di progetto in Esplora soluzioni

- Finestre **di dialogo Apri** progetto o **Nuovo** progetto

- Annidamento del progetto

- Per altre informazioni sulle funzionalità dei tipi di progetto, vedere gli argomenti seguenti:

- I tipi di progetto sono oggetti in un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] previsto. Se si usa C# per sviluppare un tipo di progetto, le classi di progetto del framework del pacchetto gestito implementano automaticamente le interfacce necessarie e consentono di ereditare tale implementazione. Per altre informazioni, vedere [Uso di Managed Package Framework per implementare un tipo di progetto (C#).](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Per gli sviluppatori C++, le classi nella libreria HierUtil funzionano in modo simile. Per altre informazioni, vedere [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type (C++) (Non in compilazione: uso delle classi di progetto HierUtil7 per implementare un tipo di progetto (C++).](/previous-versions/bb166212(v=vs.100))

- I tipi di progetto possono supportare dati diversi da file di codice sorgente tipici compilati in .exe o .dll assembly. Ad esempio, i progetti di database contengono riferimenti a file di script ed query archiviati su disco e aggiungono comandi a Esplora soluzioni per eseguire script e query su un database, ma i progetti non supportano il comportamento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilazione.  Per altre informazioni, vedere [Apertura e salvataggio di elementi di progetto.](../../extensibility/internals/opening-and-saving-project-items.md)

- Un tipo di progetto non deve usare file. Ad esempio, un tipo di progetto potrebbe archiviare tutti i dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offre ai tipi di progetto il controllo completo sulla modalità di persistenza dei dati per progetti ed elementi di progetto. Per altre informazioni, vedere [Decisioni di progettazione dei tipi di progetto.](../../extensibility/internals/project-type-design-decisions.md)

- I tipi di progetto devono fornire una *factory* del progetto, ovvero un oggetto che crea un'istanza del tipo di progetto ogni volta che viene specificato di aprire o creare un progetto basato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] su tale tipo di progetto. Per altre informazioni, vedere [Creating Project Instances By Using Project Factoryies](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- I tipi di progetto devono fornire modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa i modelli quando gli utenti creano nuovi progetti e aggiungono nuovi elementi ai progetti esistenti. Per altre informazioni, vedere Aggiunta [di modelli di progetto e di elemento di progetto.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- I tipi di progetto possono supportare più configurazioni, ad esempio Debug e Release. Gli utenti possono modificare le diverse configurazioni di un progetto usando le pagine delle proprietà fornite dall'utente. Per altre informazioni, vedere [Gestione delle opzioni di configurazione.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Vedere anche
- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)