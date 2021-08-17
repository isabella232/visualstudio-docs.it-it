---
title: Implementazione Single-File generatori | Microsoft Docs
description: Informazioni su come usare uno strumento personalizzato che implementa l'interfaccia IVsSingleFileGenerator per estendere i sistemi di progetto Visual Basic e Visual C# in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e9dd200879fb8a91eec5c63838d90f72dcad98b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069757"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
Uno strumento personalizzato, talvolta definito generatore di file singolo, può essere usato per estendere i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemi di progetto e in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Uno strumento personalizzato è un componente COM che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> l'interfaccia . Usando questa interfaccia, uno strumento personalizzato trasforma un singolo file di input in un singolo file di output. Il risultato della trasformazione può essere il codice sorgente o qualsiasi altro output utile. Due esempi di file di codice personalizzati generati dagli strumenti sono il codice generato in risposta alle modifiche in una finestra di progettazione visiva e i file generati usando Web Services Description Language (WSDL).

 Quando viene caricato uno strumento personalizzato o viene salvato il file di input, il sistema del progetto chiama il metodo e passa un riferimento a un'interfaccia di callback, in cui lo strumento può segnalare lo stato di avanzamento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> all'utente.

 Il file di output generato da uno strumento personalizzato viene aggiunto al progetto con una dipendenza dal file di input. Il sistema del progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione dello strumento personalizzato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Uno strumento personalizzato deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> l'interfaccia . Facoltativamente, gli strumenti personalizzati supportano <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> l'interfaccia per recuperare informazioni da origini diverse dal file di input. In ogni caso, prima di poter usare uno strumento personalizzato, è necessario registrarlo nel sistema o nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro di sistema locale. Per altre informazioni sulla registrazione di strumenti personalizzati, vedere [Registrazione di generatori di file singoli.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Vedi anche
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
