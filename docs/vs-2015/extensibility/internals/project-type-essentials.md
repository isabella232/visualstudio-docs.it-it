---
title: Nozioni fondamentali sui tipi di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a719ea26473874cb0d771b46ee05ea15092fb17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746462"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] include diversi tipi di progetto per le lingue, ad esempio [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consente inoltre di creare tipi di progetto.  
  
 Se si desidera solo aggiungere comandi personalizzati, gli editor o finestre degli strumenti per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], è possibile farlo senza creare un nuovo tipo di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Analogamente, se si desidera personalizzare il comportamento dell'oggetto fornito [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipi di progetto, è possibile eseguire usando sottotipi di progetto. Per altre informazioni, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
  È necessario creare un nuovo tipo di progetto per i progetti basati su un linguaggio diverso da [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] se si desidera supportare uno o più delle operazioni seguenti:  
  
- Compilazione  
  
- Distribuzione  
  
- Configurazioni multiple  
  
- Controllo del codice sorgente  
  
- Debug  
  
- Elementi del progetto in Esplora soluzioni  
  
- Il **Apri progetto** oppure **nuovo progetto** finestre di dialogo  
  
- Annidamento di progetto  
  
- Per altre informazioni sulle funzionalità dei tipi di progetto, vedere gli argomenti seguenti:  
  
- Tipi di progetto sono oggetti in un pacchetto VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si aspetta. Se si usa c# per lo sviluppo di un tipo di progetto, le classi di progetto del Framework di pacchetto gestito implementano le interfacce necessarie per l'utente e consentono di eredita tale implementazione. Per altre informazioni, vedere [usando il Framework di pacchetto gestito per implementare un tipo di progetto (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Per gli sviluppatori in C++, le classi nella libreria HierUtil funzionano in modo simile. Per altre informazioni, vedere [non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Tipi di progetto possono supportare dati diversi dai file di codice sorgente tipici che compila in un assembly .exe o DLL. Ad esempio, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetti di database contengono riferimenti a script e query file archiviati su disco e aggiungere comandi al **Esplora soluzioni** per eseguire gli script e query su un database, ma i progetti non supportano compilare un comportamento. Per altre informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Un tipo di progetto non è necessario utilizzare in tutti i file. Ad esempio, un tipo di progetto è stato possibile archiviare tutti i relativi dati in un database. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Fornisce tipi di progetto di controllo completo sul modo in cui sono persistenti i dati per progetti ed elementi del progetto. Per altre informazioni, vedere [decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
- Tipi di progetto è necessario specificare una *factory di progetto*, che è un oggetto che crea un'istanza del progetto digitare ogni volta che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verrà comunicato aprire o creare un progetto basato su tale tipo di progetto. Per altre informazioni, vedere [creazione di istanze da usando progetto le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Tipi di progetto devono fornire i modelli per progetti ed elementi del progetto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Usa i modelli quando si creano nuovi progetti e aggiungere nuovi elementi per i progetti esistenti. Per altre informazioni, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Tipi di progetto possono supportare più configurazioni, ad esempio Debug e rilascio. Gli utenti possono modificare le diverse configurazioni di un progetto utilizzando le pagine di proprietà fornito. Per altre informazioni, vedere [opzioni di configurazione Gestione](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)

