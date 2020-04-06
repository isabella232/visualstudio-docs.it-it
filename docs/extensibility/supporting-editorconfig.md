---
title: Estendere il servizio di linguaggio per supportare EditorConfigExtend language service to support EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699576"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Supporto di EditorConfig per il servizio di linguaggioSupporting EditorConfig for your language service

I file [EditorConfig](https://editorconfig.org/) consentono di descrivere le opzioni comuni dell'editor di testo, ad esempio le dimensioni del rientro, in base al progetto. Per ulteriori informazioni sul supporto di Visual Studio per i file EditorConfig, vedere [Creare impostazioni dell'editor portabile utilizzando EditorConfig](../ide/create-portable-custom-editor-options.md).

Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Tuttavia, per le modifiche, ad esempio tabulazioni e spazi, alcuni servizi di linguaggio scelgono di utilizzare un'opzione di visualizzazione di testo contestuale appropriata anziché utilizzare le impostazioni globali. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Di seguito sono riportate le modifiche necessarie per aggiornare un servizio di linguaggio per supportare i file EditorConfig, sostituendo un'opzione globale specifica del linguaggio con un'opzione contestuale:Following are the changes that are needed to update a language service to support EditorConfig files, by placing a global _language-specific_ option with _a contextual_ option:

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

## <a name="see-also"></a>Vedere anche

- [Creare impostazioni dell'editor portabile usando EditorConfigCreate portable editor settings using EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Estensione dell'editor e dei servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)
