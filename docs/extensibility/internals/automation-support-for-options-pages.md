---
title: Supporto di automazione per le pagine opzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709927"
---
# <a name="automation-support-for-options-pages"></a>Supporto di automazione per le pagine opzioni
I pacchetti VSPackage possono fornire finestre di dialogo di **Opzioni** personalizzate al menu **strumenti** (pagine**Opzioni strumenti** ) in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e possono renderle disponibili per il modello di automazione.

## <a name="tools-options-pages"></a>Opzioni del menu Strumenti (pagine)
 Per creare una pagina di **Opzioni degli strumenti** , un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione del pacchetto VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo. (O, per il codice gestito, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo).

 È facoltativo, ma consigliato, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. A questo scopo, seguire la procedura seguente:

1. Estendere l' <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato da IDispatch.

2. Restituisce un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Metodo (o per il codice gestito del <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metodo) all'oggetto derivato da IDispatch.

3. Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo in una pagina delle proprietà di un' **opzione** personalizzata, l'ambiente USA il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo per ottenere un'implementazione di automazione della pagina **Opzioni degli strumenti** personalizzata.

4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A> .

   Per un esempio di implementazione di una pagina di **Opzioni degli strumenti** personalizzata, vedere [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vedere anche
- [Esporre oggetti progetto](../../extensibility/internals/exposing-project-objects.md)
