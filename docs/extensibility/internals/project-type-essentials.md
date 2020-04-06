---
title: Informazioni di base sul tipo di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706376"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]include diversi tipi di [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]per lingue quali o . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]consente inoltre di creare tipi di progetto personalizzati.

 Se si desidera solo aggiungere comandi personalizzati, editor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]o finestre degli strumenti a , è possibile farlo senza creare un nuovo tipo di progetto. Per altre informazioni, vedere gli argomenti seguenti:

- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)

- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)

  Analogamente, se si desidera personalizzare il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] comportamento dei tipi di progetto e forniti, è possibile farlo utilizzando i sottotipi di progetto. Per ulteriori informazioni, vedere [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

  È necessario creare un nuovo tipo di progetto per [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i progetti basati su un linguaggio diverso da e se si desidera supportare uno o più degli elementi seguenti:

- Compilazione

- Distribuzione

- Configurazioni multiple

- Controllo del codice sorgente

- Debug

- Elementi di progetto in Esplora soluzioniProject items in Solution Explorer

- Finestre di dialogo **Apri progetto** o **Nuovo progetto**

- Nidificazione dei progetti

- Per ulteriori informazioni sulle funzionalità dei tipi di progetto, vedere quanto segue:

- I tipi di progetto sono oggetti in un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage che implementano il set di interfacce previsto. Se si utilizza C , per sviluppare un tipo di progetto, le classi di progetto di Framework di pacchetto gestito implementano le interfacce necessarie per l'utente e consentono di ereditare tale implementazione. Per ulteriori informazioni, vedere [Utilizzo del framework di pacchetto gestito per implementare un tipo di progetto (c'è)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Per gli sviluppatori di C, le classi nella libreria HierUtil funzionano in modo simile. Per ulteriori informazioni, vedere [Non nella compilazione: utilizzo delle classi di progetto HierUtil7 per implementare un tipo](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)di progetto (C ) .

- I tipi di progetto possono supportare dati diversi dai file di codice sorgente tipici compilati in un assembly con estensione exe o dll. Ad esempio, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i progetti di database contengono riferimenti ai file di script e di query archiviati su disco e aggiungono comandi a **Esplora soluzioni** per eseguire gli script e le query su un database, ma i progetti non supportano il comportamento di compilazione. Per ulteriori informazioni, vedere [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

- Un tipo di progetto non deve utilizzare i file. Ad esempio, un tipo di progetto potrebbe archiviare tutti i dati in un database. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]offre ai tipi di progetto il controllo completo sul modo in cui mantengono i dati per i progetti e gli elementi di progetto. Per ulteriori informazioni, consultate [Decisioni di progettazione dei](../../extensibility/internals/project-type-design-decisions.md)tipi di progetto .

- I tipi di progetto devono fornire una factory del *progetto,* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ovvero un oggetto che crea un'istanza del tipo di progetto ogni volta che viene detto di aprire o creare un progetto basato su tale tipo di progetto. Per ulteriori informazioni, vedere Creazione di istanze di [progetto tramite Factory Factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)di progetto .

- I tipi di progetto devono fornire modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilizza i modelli quando gli utenti creano nuovi progetti e aggiungono nuovi elementi ai progetti esistenti. Per ulteriori informazioni, vedere Aggiunta di modelli di [progetto e di elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)di progetto .

- I tipi di progetto possono supportare più configurazioni, ad esempio Debug e Release.Project types can support multiple configurations, such as Debug and Release. Gli utenti possono modificare le diverse configurazioni di un progetto utilizzando le pagine delle proprietà fornite. Per ulteriori informazioni, vedere [Gestione delle opzioni](../../extensibility/internals/managing-configuration-options.md)di configurazione .

## <a name="see-also"></a>Vedere anche
- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)
