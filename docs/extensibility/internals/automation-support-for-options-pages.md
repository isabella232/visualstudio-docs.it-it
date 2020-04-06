---
title: Supporto dell'automazione per le pagine delle opzioni Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709927"
---
# <a name="automation-support-for-options-pages"></a>Supporto di automazione per le pagine Opzioni
VSPackage possono fornire **opzioni** personalizzate finestre di dialogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per il **strumenti** menu **(pagine Opzioni degli strumenti)** in e possono renderli disponibili per il modello di automazione.

## <a name="tools-options-pages"></a>Opzioni del menu Strumenti (pagine)
 Per creare una pagina **di opzioni** degli strumenti, un VSPackage deve fornire un'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> del controllo utente restituito all'ambiente tramite l'implementazione del metodo del pacchetto VSPackage.To create a Tools Options page, a VSPackage must provide a user control implementation returned to the environment through the VSPackage's implementation of the method. (Oppure, per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> codice gestito, il metodo.)

 È facoltativo, ma fortemente consigliato, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. È possibile farlo con i seguenti passaggi:

1. Estendere <xref:EnvDTE._DTE.Properties%2A> l'oggetto tramite l'implementazione di un IDispatch-oggetto derivato.

2. Restituire un'implementazione del metodo (o per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metodo) per il IDispatch-oggetto derivato.

3. Quando un consumer <xref:EnvDTE._DTE.Properties%2A> di automazione chiama il metodo in <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> una pagina delle proprietà **Option** personalizzata, l'ambiente utilizza il metodo per ottenere un'implementazione di automazione della pagina Opzioni **degli strumenti** personalizzata.

4. L'oggetto di automazione del pacchetto <xref:EnvDTE.Property> VSPackage <xref:EnvDTE._DTE.Properties%2A>viene quindi utilizzato per fornire ogni restituito da .

   Per un esempio di implementazione di una pagina delle **opzioni degli strumenti** personalizzata, vedere Esempi di [VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vedere anche
- [Esporre gli oggetti del progetto](../../extensibility/internals/exposing-project-objects.md)
