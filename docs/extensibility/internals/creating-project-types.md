---
title: Creazione di tipi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948e8f5fe5cb2131984c407a10d011ffba1e4655
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983534"
---
# <a name="create-project-types"></a>Creare tipi di progetto
È possibile estendere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creando un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere alcuni concetti e completare una serie di passaggi. Gli argomenti seguenti forniscono una panoramica su come creare tipi di progetto.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Decisioni di progettazione di tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)  
 Illustra l'elemento, la persistenza del file di progetto e impegno meccanico sulle scelte di progettazione da prendere prima di creare un nuovo tipo di progetto.  
  
 [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Viene fornita una panoramica dei passaggi da seguire per creare un nuovo tipo di progetto che supporta tali attività di programmazione come la modifica del codice e la compilazione, creazione, debug e distribuzione di applicazioni nel progetto.  
  
 [Creare istanze del progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Vengono fornite informazioni su come fornire e utilizzare una factory di progetto per creare istanze di un nuovo progetto.  
  
 [Registrare un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)  
 Vengono forniti esempi di codice delle istruzioni dal Registro di sistema che forniscono i percorsi predefiniti e i dati e una tabella che contengono voci dallo script del Registro di sistema per ogni istruzione.  
  
 [Persistenza del progetto](../../extensibility/internals/project-persistence.md)  
 Viene illustrato l'utilizzo di `IPersistFileFormat` per rendere persistenti i file e gli oggetti non basate su file di progetto.  
  
 [Uso di MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descrive come è possibile usare il tipo di progetto di [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] per consentire agli utenti di compilazione dal motore di compilazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e nella riga di comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto di strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Viene illustrata l'architettura di codice, strumenti per la visualizzazione, ad esempio la **Visualizzatore oggetti** e **Visualizzazione classi** finestra. Descrive le interfacce e metodi che vengono usati per implementare l'esplorazione degli oggetti in un pacchetto VSPackage.  
  
 [Aggiungere al progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Illustra l'importanza che i progetti vengono riprodotte nel determinare quale editor da utilizzare quando un elemento del progetto viene aperto e modo in cui le risorse del progetto possono essere modificate.  
  
 [Installare i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Viene illustrato come fornire la propria identità univoca del pacchetto VSPackage e come eseguire il wrapping delle DLL di VSPackage e altre informazioni in un pacchetto Windows Installer (*. Identità del servizio gestito* file) per la distribuzione ai clienti.  
  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Viene descritto come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerarchie di viste e gli indirizzi.  
  
 [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)  
 Viene fornita una panoramica di un pacchetto VSPackage, un oggetto COM installabile che estende il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e viene illustrato come implementare il proprio pacchetto VSPackage.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Illustra come usare i progetti per modificare il codice, compilare e codice, compilare ed eseguire e il debug del codice e vengono forniti collegamenti ad argomenti dettagliati su come creare tipi di progetto.