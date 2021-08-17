---
title: Esposizione di tipi alle finestre di progettazione visiva | Microsoft Docs
description: Informazioni su come esporre le definizioni di classi e tipi, incluse quelle negli strumenti personalizzati, in modo Visual Studio renderle disponibili alle finestre di progettazione visiva.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ffee5f17192cc14346f9da52ce32551dea6daded
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094854"
---
# <a name="expose-types-to-visual-designers"></a>Esporre i tipi alle finestre di progettazione visiva
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve avere accesso alle definizioni di classi e tipi in fase di progettazione per visualizzare una finestra di progettazione visiva. Le classi vengono caricate da un set predefinito di assembly che includono il set di dipendenze completo del progetto corrente (riferimenti e relative dipendenze). Può anche essere necessario per le finestre di progettazione visive accedere a classi e tipi definiti nei file generati da strumenti personalizzati.

 I sistemi di progetto e forniscono il supporto per l'accesso a classi e tipi generati tramite file [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] eseguibili portabili temporanei (FILE PE temporanei). Qualsiasi file generato da uno strumento personalizzato può essere compilato in un assembly temporaneo in modo che i tipi possano essere caricati da tali assembly ed esposti alle finestre di progettazione. L'output di ogni strumento personalizzato viene compilato in un file PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo dalla compilazione o meno del file generato. Anche se un progetto potrebbe non essere compilato nel suo complesso, i singoli PE temporanei potrebbero essere ancora disponibili per le finestre di progettazione.

 Il sistema del progetto fornisce il supporto completo per il rilevamento delle modifiche al file di output di uno strumento personalizzato, a condizione che queste modifiche siano il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo pe temporaneo e le notifiche appropriate vengono inviate ai progettisti.

> [!NOTE]
> Poiché il file di generazione dell'eseguibile del programma temporaneo viene eseguito in background, non viene segnalato alcun errore all'utente se la compilazione ha esito negativo.

 Gli strumenti personalizzati che sfruttano il supporto pe temporaneo devono seguire le regole seguenti:

- **GeneratesDesignTimeSource** deve essere impostato su 1 nel Registro di sistema.

     Senza questa impostazione non viene eseguito alcun file eseguibile del programma.

- Il codice generato deve essere nella stessa lingua dell'impostazione globale del progetto.

     Il file PE temporaneo viene compilato indipendentemente da ciò che lo strumento personalizzato segnala come estensione richiesta in , purché <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> **GeneratesDesignTimeSource** sia impostato su 1 nel Registro di sistema. Non è necessario che l'estensione sia *vb*, *cs* o *jsl*. può essere qualsiasi estensione.

- Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato da solo usando solo il set di riferimenti presenti nel progetto al termine <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> dell'esecuzione.

     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Pertanto, uno strumento personalizzato che usa un file PE temporaneo deve generare file di output che possono essere compilati indipendentemente da altri file nel progetto.

## <a name="see-also"></a>Vedi anche
- [Introduzione all'oggetto BuildManager](/previous-versions/8f9kffa8(v=vs.140))
- [Implementare generatori a file singolo](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrare generatori a file singolo](../../extensibility/internals/registering-single-file-generators.md)