---
title: Implementazione di generatori a file singolo Documenti Microsoft
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
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707661"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
Uno strumento personalizzato, talvolta definito generatore di file singolo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] può [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]essere utilizzato per estendere i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemi e in . Uno strumento personalizzato è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> componente COM che implementa l'interfaccia. Utilizzando questa interfaccia, uno strumento personalizzato trasforma un singolo file di input in un singolo file di output. Il risultato della trasformazione può essere codice sorgente o qualsiasi altro output utile. Due esempi di file di codice personalizzati generati dagli strumenti sono i file di codice generati dal codice in risposta alle modifiche apportate in una finestra di progettazione visiva e i file generati utilizzando il linguaggio WSDL (Web Services Description Language).

 Quando viene caricato uno strumento personalizzato o il file di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> input viene salvato, <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> il sistema del progetto chiama il metodo e passa un riferimento a un'interfaccia di callback, in base alla quale lo strumento può segnalare lo stato di avanzamento all'utente.

 Il file di output generato dallo strumento personalizzato viene aggiunto al progetto con una dipendenza dal file di input. Il sistema del progetto determina automaticamente il nome del file di output, in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>base alla stringa restituita dall'implementazione dello strumento personalizzato di .

 Uno strumento personalizzato <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> deve implementare l'interfaccia. Facoltativamente, gli strumenti <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> personalizzati supportano l'interfaccia per recuperare informazioni da origini diverse dal file di input. In ogni caso, prima di poter utilizzare uno strumento personalizzato, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è necessario registrarlo con il sistema o nel Registro di sistema locale. Per ulteriori informazioni sulla registrazione di strumenti personalizzati, vedere [Registrazione di generatori](../../extensibility/internals/registering-single-file-generators.md)di file singoli .

## <a name="see-also"></a>Vedere anche
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
