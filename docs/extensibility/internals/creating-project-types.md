---
title: Creazione di tipi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709073"
---
# <a name="create-project-types"></a>Creare tipi di progetto
È possibile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estendere creando un nuovo tipo di progetto. Per creare un nuovo tipo di progetto, è necessario comprendere diversi concetti e completare una serie di passaggi. Negli argomenti riportati di seguito viene fornita una panoramica della creazione di tipi di progetto.

## <a name="in-this-section"></a>Contenuto della sezione
- [Decisioni di progettazione del tipo di progetto](../../extensibility/internals/project-type-design-decisions.md)

 Vengono illustrati l'elemento, la persistenza del file di progetto e le decisioni di progettazione meccanica di impegno che è necessario prendere prima di creare un nuovo tipo di progetto.

- [Elenco di controllo: creare nuovi tipi di progettoChecklist: Create new project types](../../extensibility/internals/checklist-creating-new-project-types.md)

 Viene fornita una panoramica dei passaggi da seguire per creare un nuovo tipo di progetto che supporti attività di programmazione quali la modifica del codice e la compilazione, la compilazione, il debug e la distribuzione di applicazioni nel progetto.

- [Creare istanze di progetto utilizzando le factory di progettoCreate project instances by using project factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Vengono fornite informazioni su come fornire e utilizzare una factory del progetto per creare istanze di un nuovo progetto.

- [Registrare un tipo di progettoRegister a project type](../../extensibility/internals/registering-a-project-type.md)

 Vengono forniti esempi di codice di istruzioni del Registro di sistema che forniscono dati e percorsi predefiniti e una tabella contenente le voci dello script del Registro di sistema per ogni istruzione.

- [Persistenza del progetto](../../extensibility/internals/project-persistence.md)

 Viene illustrato `IPersistFileFormat` l'utilizzo di per rendere persistenti gli oggetti di progetto basati su file e non basati su file.

- [Usare MSBuild](../../extensibility/internals/using-msbuild.md)

 Viene descritto come il tipo [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] di progetto può [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzare il motore di compilazione per consentire agli utenti di compilare da e nella riga di comando.

## <a name="related-sections"></a>Sezioni correlate
- [Supporta gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Viene illustrata l'architettura degli strumenti di visualizzazione del codice, ad esempio il **Visualizzatore oggetti** e la finestra **Visualizzazione classi.** Descrive le interfacce e i metodi utilizzati per implementare l'esplorazione degli oggetti in un pacchetto VSPackage.

- [Aggiungere modelli di progetto e di elemento di progettoAdd project and project item templates](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Viene illustrato il significato che i progetti svolgono nel determinare quale editor viene utilizzato quando viene aperto un elemento di progetto e come è possibile modificare le risorse del progetto.

- [Installare i pacchetti VSPackage con Windows InstallerInstall VSPackages with Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Viene illustrato come assegnare il pacchetto VSPackage la propria identità univoca e come eseguire il wrapping delle DLL VSPackage e altre informazioni in un pacchetto di Windows Installer (*. MSI)* per la distribuzione ai clienti.

- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Viene descritto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come gerarchie di viste e indirizzi.

- [Pacchetti VSPackage](../../extensibility/internals/vspackages.md)

 Fornisce una panoramica di un vsPackage, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oggetto COM installabile che estende l'ambiente e viene illustrato come implementare il proprio VSPackage.

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Viene illustrato come utilizzare i progetti per modificare il codice, compilare e compilare codice ed eseguire ed eseguire il debug del codice e vengono forniti collegamenti ad argomenti dettagliati sulla creazione di tipi di progetto.
