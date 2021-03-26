---
title: Creazione di tipi di progetto | Microsoft Docs
description: Informazioni su come estendere Visual Studio tramite la progettazione, la creazione e la registrazione di un nuovo tipo di progetto che supporta le attività di programmazione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 5984afd2879f94a73ef02f77a85501c50f55bc93
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056818"
---
# <a name="create-project-types"></a>Creazione di tipi di progetto
È possibile estendere creando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere alcuni concetti e completare una serie di passaggi. Negli argomenti seguenti viene fornita una panoramica su come creare i tipi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Decisioni di progettazione del tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)

 Vengono illustrate le decisioni relative all'elemento, alla persistenza dei file di progetto e al progetto Mechanical commit che è necessario apportare prima di creare un nuovo tipo di progetto.

- [Elenco di controllo: creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)

 Viene fornita una panoramica dei passaggi che è necessario seguire per creare un nuovo tipo di progetto che supporta le attività di programmazione come la modifica del codice e la compilazione, la compilazione, il debug e la distribuzione di applicazioni nel progetto.

- [Creare istanze di progetto tramite Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Vengono fornite informazioni su come fornire e utilizzare una factory di progetto per creare istanze di un nuovo progetto.

- [Registrare un tipo di progetto](../../extensibility/internals/registering-a-project-type.md)

 Fornisce esempi di codice di istruzioni dal registro di sistema che forniscono i percorsi e i dati predefiniti e una tabella che contiene voci dello script del registro di sistema per ogni istruzione.

- [Persistenza progetto](../../extensibility/internals/project-persistence.md)

 Viene illustrato l'utilizzo di `IPersistFileFormat` per salvare in modo permanente sia gli oggetti progetto di file che quelli non basati su file.

- [Usare MSBuild](../../extensibility/internals/using-msbuild.md)

 Descrive il modo in cui il tipo di progetto può usare il [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] motore di compilazione per consentire agli utenti di compilare da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e nella riga di comando.

## <a name="related-sections"></a>Sezioni correlate
- [Supporto degli strumenti per l'esplorazione di simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Viene illustrata l'architettura degli strumenti di visualizzazione del codice, ad esempio il **Visualizzatore oggetti** e la finestra di **Visualizzazione classi** . Vengono descritte le interfacce e i metodi utilizzati per implementare l'esplorazione degli oggetti in un VSPackage.

- [Aggiungere modelli di progetti e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Viene illustrato il significato che i progetti svolgono per determinare quale editor viene utilizzato quando viene aperto un elemento del progetto e come possono essere modificate le risorse del progetto.

- [Installare VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Viene illustrato come assegnare al VSPackage una propria identità univoca e come eseguire il wrapping delle dll VSPackage e di altre informazioni in un pacchetto di Windows Installer (*. File MSI* ) per la distribuzione ai clienti.

- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Viene descritto come visualizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e indirizzare le gerarchie.

- [VSPackages](../../extensibility/internals/vspackages.md)

 Viene fornita una panoramica di un pacchetto VSPackage, un oggetto COM installabile che estende l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente e viene illustrato come implementare un pacchetto VSPackage personalizzato.

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Viene illustrato come utilizzare i progetti per modificare codice, compilare e compilare codice, eseguire ed eseguire il debug del codice e vengono forniti collegamenti ad argomenti dettagliati sulla creazione di tipi di progetto.
