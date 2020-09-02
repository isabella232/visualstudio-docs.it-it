---
title: Tipi di progetto Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704069"
---
# <a name="project-type-essentials"></a>Nozioni fondamentali sui tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] include diversi tipi di progetto per linguaggi quali [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consente inoltre di creare tipi di progetto personalizzati.  
  
 Se si desidera solo aggiungere comandi, editor o finestre degli strumenti personalizzati a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , è possibile farlo senza creare un nuovo tipo di progetto. Per altre informazioni, vedere gli argomenti seguenti:  
  
- [Comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Estensioni dell'editor e dei servizi di linguaggio](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Analogamente, se si desidera personalizzare il comportamento dei tipi di [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetto e forniti [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , è possibile utilizzare i sottotipi di progetto. Per altre informazioni, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
  È necessario creare un nuovo tipo di progetto per i progetti basati su una lingua diversa da [!INCLUDE[csprcs](../../includes/csprcs-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] se si desidera supportare uno o più degli elementi seguenti:  
  
- Compilare  
  
- Distribuzione  
  
- Configurazioni multiple  
  
- Controllo del codice sorgente  
  
- Debug  
  
- Elementi di progetto in Esplora soluzioni  
  
- Finestre di dialogo **Apri progetto** o **nuovo progetto**  
  
- Annidamento del progetto  
  
- Per ulteriori informazioni sulle funzionalità dei tipi di progetto, vedere gli argomenti seguenti:  
  
- I tipi di progetto sono oggetti in un VSPackage che implementano il set di interfacce [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] previsto. Se si utilizza C# per sviluppare un tipo di progetto, le classi di progetto del Framework di pacchetto gestito implementano le interfacce necessarie per l'utente e consentono di ereditare l'implementazione. Per ulteriori informazioni, vedere [utilizzo del Framework di pacchetto gestito per implementare un tipo di progetto (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Per gli sviluppatori C++, le classi nella libreria HierUtil funzionano in modo simile. Per altre informazioni, vedere [not in Build: uso di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- I tipi di progetto possono supportare dati diversi dai normali file di codice sorgente che si compilano in un assembly con estensione exe o dll. Ad esempio, i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetti di database contengono riferimenti a file di script e di query archiviati su disco e aggiungono comandi a **Esplora soluzioni** per eseguire gli script e le query su un database, ma i progetti non supportano il comportamento di compilazione. Per ulteriori informazioni, vedere [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Un tipo di progetto non deve necessariamente usare i file. Un tipo di progetto, ad esempio, può archiviare tutti i relativi dati in un database. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce ai tipi di progetto il controllo completo sulla modalità di mantenimento dei dati per progetti ed elementi di progetto. Per altre informazioni, vedere [decisioni di progettazione dei tipi di progetto](../../extensibility/internals/project-type-design-decisions.md).  
  
- I tipi di progetto devono fornire una *Factory del progetto*, ovvero un oggetto che crea un'istanza del tipo di progetto ogni volta che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene richiesto di aprire o creare un progetto basato su tale tipo di progetto. Per altre informazioni, vedere [creazione di istanze di progetto tramite Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- I tipi di progetto devono fornire modelli per progetti ed elementi di progetto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] USA i modelli quando gli utenti creano nuovi progetti e aggiungono nuovi elementi ai progetti esistenti. Per ulteriori informazioni, vedere [aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- I tipi di progetto possono supportare più configurazioni, ad esempio debug e release. Gli utenti possono modificare le diverse configurazioni di un progetto utilizzando le pagine delle proprietà fornite. Per ulteriori informazioni, vedere [gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)
