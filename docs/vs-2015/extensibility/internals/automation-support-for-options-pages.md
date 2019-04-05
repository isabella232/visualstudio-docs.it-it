---
title: Supporto di automazione per le pagine di opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965059"
---
# <a name="automation-support-for-options-pages"></a>Supporto dell'automazione per le pagine di opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I VSPackage possono fornire personalizzata **opzioni** alle finestre di dialogo per il **Tools** menu (pagine Opzioni del menu Strumenti) in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e può renderli disponibili per il modello di automazione.  
  
## <a name="tools-options-pages"></a>Pagine delle opzioni degli strumenti  
 Per creare un **opzioni degli strumenti** pagina, un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione di VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo (o per codice gestito il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo).  
  
 È facoltativo, ma fortemente consigliato, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. È possibile farlo tramite la procedura seguente:  
  
1. Estendere il <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato IDispatch.  
  
2. Restituiscono un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo (o per il codice gestito il <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> (metodo)) per l'oggetto derivato IDispatch.  
  
3. Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo su un oggetto personalizzato **opzione** pagina delle proprietà, l'ambiente Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo per ottenere un oggetto personalizzato **opzioni del menu Strumenti** automazione della pagina implementazione.  
  
4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire a ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A>.  
  
   Per un esempio di implementazione di una pagina di opzioni del menu strumenti personalizzata, vedere [esempi di VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)
