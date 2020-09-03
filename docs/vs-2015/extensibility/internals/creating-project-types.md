---
title: Creazione di tipi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155037"
---
# <a name="creating-project-types"></a>Creazione di tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile estendere creando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere alcuni concetti e completare una serie di passaggi. Negli argomenti seguenti viene fornita una panoramica su come creare i tipi di progetto.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Decisioni di progettazione relative al tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)  
 Vengono illustrate le decisioni relative all'elemento, alla persistenza dei file di progetto e al progetto Mechanical commit che è necessario apportare prima di creare un nuovo tipo di progetto.  
  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Viene fornita una panoramica dei passaggi che è necessario seguire per creare un nuovo tipo di progetto che supporta attività di programmazione come la modifica del codice e la compilazione, la compilazione, il debug e la distribuzione di applicazioni nel progetto.  
  
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Vengono fornite informazioni su come fornire e utilizzare una factory di progetto per creare istanze di un nuovo progetto.  
  
 [Registrazione di un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)  
 Fornisce esempi di codice di istruzioni dal registro di sistema che forniscono i percorsi e i dati predefiniti e una tabella che contiene voci dello script del registro di sistema per ogni istruzione.  
  
 [Salvataggio permanente dei progetti](../../extensibility/internals/project-persistence.md)  
 Viene illustrato l'utilizzo di `IPersistFileFormat` per salvare in modo permanente sia gli oggetti progetto di file che quelli non basati su file.  
  
 [Uso di MSBuild](../../extensibility/internals/using-msbuild.md)  
 Descrive il modo in cui il tipo di progetto può usare il [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] motore di compilazione per consentire agli utenti di compilare da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e nella riga di comando.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Viene illustrata l'architettura degli strumenti di visualizzazione del codice, ad esempio il **Visualizzatore oggetti** e la finestra di **Visualizzazione classi** . Vengono descritte le interfacce e i metodi utilizzati per implementare l'esplorazione degli oggetti in un VSPackage.  
  
 [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Viene illustrato il significato che i progetti svolgono per determinare quale editor viene utilizzato quando viene aperto un elemento del progetto e come possono essere modificate le risorse del progetto.  
  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Viene illustrato come assegnare al VSPackage una propria identità univoca e come eseguire il wrapping delle dll VSPackage e di altre informazioni in un pacchetto di Windows Installer (. File MSI) per la distribuzione ai clienti.  
  
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Viene descritto come visualizzare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e indirizzare le gerarchie.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Viene fornita una panoramica di un pacchetto VSPackage, un oggetto COM installabile che estende l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente e viene illustrato come implementare un pacchetto VSPackage personalizzato.  
  
 [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)  
 Viene illustrato come utilizzare i progetti per modificare codice, compilare e compilare codice, eseguire ed eseguire il debug del codice e vengono forniti collegamenti ad argomenti dettagliati sulla creazione di tipi di progetto.
