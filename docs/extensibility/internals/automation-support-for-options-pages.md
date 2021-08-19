---
title: Supporto di Automazione per le pagine delle opzioni | Microsoft Docs
description: Informazioni su come rendere disponibili le pagine opzioni degli strumenti personalizzate in VSPackage per il Visual Studio di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 789239eb2d11ed2abaec3d031dd7bce0da2cbfce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159269"
---
# <a name="automation-support-for-options-pages"></a>Supporto dell'automazione per le pagine Opzioni
I pacchetti VSPackage possono fornire **finestre** di dialogo Opzioni personalizzate al **menu** Strumenti **(pagine** Opzioni strumenti) in e possono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] renderle disponibili per il modello di automazione.

## <a name="tools-options-pages"></a>Opzioni del menu Strumenti (pagine)
 Per creare una **pagina Opzioni degli** strumenti, un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione del metodo del pacchetto VSPackage. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Oppure, per il codice gestito, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo .

 È facoltativo, ma fortemente consigliato, consentire l'accesso a questa nuova pagina tramite il modello di automazione. A questo scopo, seguire la procedura seguente:

1. Estendere <xref:EnvDTE._DTE.Properties%2A> l'oggetto tramite l'implementazione di un oggetto derivato da IDispatch.

2. Restituire un'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> del metodo (o per il codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metodo ) all'oggetto derivato da IDispatch.

3. Quando un consumer di automazione chiama il metodo in una pagina delle proprietà Option personalizzata, l'ambiente usa il metodo per ottenere l'implementazione di automazione di una pagina <xref:EnvDTE._DTE.Properties%2A> Strumenti  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> personalizzata. 

4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire ogni <xref:EnvDTE.Property> oggetto restituito da <xref:EnvDTE._DTE.Properties%2A> .

   Per un esempio di implementazione di una pagina **Opzioni degli** strumenti personalizzata, vedere Esempi [di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vedi anche
- [Esporre oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)
