---
title: Supporto di Automazione per le pagine di opzioni | Microsoft Docs
description: Informazioni su come rendere disponibili le pagine di opzioni degli strumenti personalizzate nei pacchetti VSPackage per il Visual Studio di automazione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 5a4f6b33b7a5e17c610831db5d4387065915ea00
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901656"
---
# <a name="automation-support-for-options-pages"></a>Supporto dell'automazione per le pagine Options
I pacchetti VSPackage possono fornire **finestre** di dialogo Opzioni personalizzate nel **menu** Strumenti **(pagine** Opzioni strumenti) in e renderli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] disponibili per il modello di automazione.

## <a name="tools-options-pages"></a>Opzioni del menu Strumenti (pagine)
 Per creare una **pagina Opzioni** degli strumenti, un PACCHETTO VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione del metodo del pacchetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSPackage. Oppure, per il codice gestito, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo .

 È facoltativo, ma consigliabile, consentire l'accesso a questa nuova pagina tramite il modello di automazione. A questo scopo, seguire la procedura seguente:

1. Estendere <xref:EnvDTE._DTE.Properties%2A> l'oggetto tramite l'implementazione di un oggetto derivato da IDispatch.

2. Restituisce un'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> del metodo (o per il codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metodo ) all'oggetto derivato da IDispatch.

3. Quando un consumer di automazione chiama il metodo in una pagina delle proprietà Option personalizzata, l'ambiente usa il metodo per ottenere <xref:EnvDTE._DTE.Properties%2A>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> l'implementazione  di automazione di una pagina Opzioni degli strumenti personalizzata.

4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire ogni <xref:EnvDTE.Property> oggetto restituito da <xref:EnvDTE._DTE.Properties%2A> .

   Per un esempio di implementazione di una pagina **Opzioni degli** strumenti personalizzata, vedere Esempi [di VSSDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

## <a name="see-also"></a>Vedere anche
- [Esporre oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)
