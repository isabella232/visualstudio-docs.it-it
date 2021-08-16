---
title: Estendere il servizio di linguaggio per supportare EditorConfig
description: Informazioni sulle modifiche da apportare per aggiornare un servizio di linguaggio per supportare i file EditorConfig. Sostituire un'opzione specifica della lingua globale con un'opzione contestuale.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2cdb6869435acf3a9e059b66492479b12135ad16671a38d9c0c4d7dcf76ff63b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388123"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Supporto di EditorConfig per il servizio di linguaggio

[I file EditorConfig](https://editorconfig.org/) consentono di descrivere le opzioni comuni dell'editor di testo, ad esempio le dimensioni del rientro, in base al progetto. Per altre informazioni sul Visual Studio per i file EditorConfig, vedere Creare impostazioni dell'editor portabile [usando EditorConfig](../ide/create-portable-custom-editor-options.md).

Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Tuttavia, per le modifiche, ad esempio tabulazioni e spazi, alcuni servizi linguistici scelgono di usare un'opzione di visualizzazione del testo contestuale appropriata anziché usare le impostazioni globali. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Di seguito sono riportate le modifiche necessarie per aggiornare un servizio di  linguaggio per supportare i file EditorConfig, sostituendo un'opzione globale specifica del linguaggio con un'opzione _contestuale:_

## <a name="indent-style"></a>Stile rientro

Opzioni specifiche della lingua | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Dimensione rientro

Opzioni specifiche della lingua | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Dimensione tabulazione

Opzioni specifiche della lingua | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Vedi anche

- [Creare impostazioni dell'editor portabile usando EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Estensione dell'editor e dei servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)
