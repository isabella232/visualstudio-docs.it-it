---
title: Estensione di un servizio di linguaggio per il supporto di EditorConfig in Visual Studio | Microsoft Docs
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 047545f3b2ab3c08b84fbb4af95a46c44655f1cd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981295"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Supporto di EditorConfig per il servizio di linguaggio

[EditorConfig](http://editorconfig.org/) file consentono di descrivere opzioni dell'editor di testo comuni, ad esempio la dimensione del rientro, in base al progetto. Per altre informazioni sul supporto di Visual Studio per i file EditorConfig, vedere [creare le impostazioni di portabili per l'editor con EditorConfig](../ide/create-portable-custom-editor-options.md).

Nella maggior parte dei casi, quando si implementa un servizio di linguaggio di Visual Studio, non è necessario alcun intervento aggiuntivo per supportare le proprietà universali di EditorConfig. L'editor principale individua e legge automaticamente il file con estensione editorconfig quando gli utenti aprono i file e imposta le opzioni appropriate per buffer di testo e visualizzazione. Tuttavia, per le modifiche, ad esempio spazi e tabulazioni, alcuni servizi di linguaggio scelgono per utilizzare un'opzione di visualizzazione testo contestuale appropriata anziché utilizzare le impostazioni globali. In questi casi il servizio di linguaggio deve essere aggiornato in modo da supportare i file EditorConfig.

Di seguito sono le modifiche necessarie per aggiornare un servizio di linguaggio per supportare i file di EditorConfig, sostituendo globale _specifiche della lingua_ con un _contestuali_ opzione:

## <a name="indent-style"></a>Stile rientro

Opzioni specifiche del linguaggio | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Dimensione rientro

Opzioni specifiche del linguaggio | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Dimensione tabulazione

Opzioni specifiche del linguaggio | Opzioni contestuali
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Vedere anche

[Creare impostazioni portabili per l'editor con EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Estensione di editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)