---
title: Implementazione di generatori di Single-File | Microsoft Docs
description: Informazioni su come usare uno strumento personalizzato che implementa l'interfaccia IVsSingleFileGenerator per estendere i sistemi di progetto Visual Basic e Visual C# in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 373536844e3572e2e61b56c1b86f3e00ed47845d
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761244"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
Uno strumento personalizzato, talvolta denominato generatore di file singolo, può essere utilizzato per estendere i sistemi di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetto e in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Uno strumento personalizzato è un componente COM che implementa l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Utilizzando questa interfaccia, uno strumento personalizzato trasforma un singolo file di input in un unico file di output. Il risultato della trasformazione può essere codice sorgente o qualsiasi altro output utile. Due esempi di file di codice generati da strumenti personalizzati sono rappresentati dal codice generato in risposta alle modifiche in una finestra di progettazione visiva e ai file generati utilizzando Web Services Description Language (WSDL).

 Quando viene caricato uno strumento personalizzato o il file di input viene salvato, il sistema del progetto chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodo e passa un riferimento a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaccia di callback, in modo che lo strumento possa segnalare lo stato di avanzamento all'utente.

 Il file di output generato dallo strumento personalizzato viene aggiunto al progetto con una dipendenza dal file di input. Il sistema del progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione dello strumento personalizzato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Uno strumento personalizzato deve implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Facoltativamente, gli strumenti personalizzati supportano l' <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaccia per recuperare le informazioni da origini diverse da quelle del file di input. In ogni caso, prima di poter usare uno strumento personalizzato, è necessario registrarlo nel sistema o nel registro di sistema [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] locale. Per ulteriori informazioni sulla registrazione di strumenti personalizzati, vedere la pagina relativa alla [registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Vedi anche
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
