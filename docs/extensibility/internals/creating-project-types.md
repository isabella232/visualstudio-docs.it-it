---
title: Creazione Project tipi | Microsoft Docs
description: Informazioni su come estendere Visual Studio progettando, creando e registrando un nuovo tipo di progetto che supporta le attività di programmazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d4793bd69ffba676081139d61c0d81bcef4c336c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086664"
---
# <a name="create-project-types"></a>Creare tipi di progetto
È possibile estendere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] creando un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere diversi concetti e completare una serie di passaggi. Negli argomenti seguenti viene fornita una panoramica di come creare tipi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Project di progettazione dei tipi](../../extensibility/internals/project-type-design-decisions.md)

 Vengono illustrati l'elemento, la persistenza del file di progetto e le decisioni di progettazione del meccanismo di impegno che è necessario prendere prima di creare un nuovo tipo di progetto.

- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)

 Viene fornita una panoramica dei passaggi da eseguire per creare un nuovo tipo di progetto che supporta attività di programmazione quali la modifica del codice e la compilazione, la compilazione, il debug e la distribuzione di applicazioni nel progetto.

- [Creare istanze del progetto usando le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Fornisce informazioni su come fornire e usare una factory del progetto per creare istanze di un nuovo progetto.

- [Registrare un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)

 Vengono forniti esempi di codice di istruzioni del Registro di sistema che forniscono percorsi e dati predefiniti e una tabella che contiene voci dello script del Registro di sistema per ogni istruzione.

- [Project persistenza](../../extensibility/internals/project-persistence.md)

 Viene illustrato l'uso di per rendere persistenti sia gli oggetti di progetto basati su `IPersistFileFormat` file che non basati su file.

- [Usare MSBuild](../../extensibility/internals/using-msbuild.md)

 Descrive come il tipo di progetto può usare il motore di compilazione per consentire agli utenti di compilare da [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] e dalla riga di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando.

## <a name="related-sections"></a>Sezioni correlate
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Viene illustrata l'architettura degli strumenti di visualizzazione del codice, ad esempio **visualizzatore** oggetti **e Visualizzazione classi** finestra. Descrive le interfacce e i metodi usati per implementare l'esplorazione di oggetti in un VSPackage.

- [Aggiungere modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Viene illustrato il significato dei progetti per determinare quale editor viene usato quando viene aperto un elemento di progetto e come è possibile modificare le risorse del progetto.

- [Installare i pacchetti VSPackage con il Windows installazione](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Illustra come assegnare al pacchetto VSPackage una propria identità univoca e come eseguire il wrapping delle DLL VSPackage e di altre informazioni in un pacchetto del programma di installazione di Windows (file *.MSI)* per la distribuzione ai clienti.

- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Viene descritto il modo in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cui le visualizzazioni e gli indirizzi delle gerarchie.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Fornisce una panoramica di un PACCHETTO VSPackage, un oggetto COM installabile che estende l'ambiente e illustra come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementare un pacchetto VSPackage personalizzato.

- [Project seguenti](../../extensibility/internals/project-types.md)

 Viene illustrato come usare i progetti per modificare il codice, compilare e compilare codice, eseguire ed eseguire il codice e come eseguirne il debug e vengono forniti collegamenti ad argomenti dettagliati su come creare tipi di progetto.
