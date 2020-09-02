---
title: Supporto di automazione per le pagine opzioni | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157239"
---
# <a name="automation-support-for-options-pages"></a>Supporto dell'automazione per le pagine di opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I pacchetti VSPackage possono fornire finestre di dialogo di **Opzioni** personalizzate al menu **strumenti** (pagine Opzioni strumenti) in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e possono renderle disponibili per il modello di automazione.  
  
## <a name="tools-options-pages"></a>Pagine Opzioni strumenti  
 Per creare una pagina di **Opzioni degli strumenti** , un pacchetto VSPackage deve fornire un'implementazione del controllo utente restituita all'ambiente tramite l'implementazione del pacchetto VSPackage del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo, o per il metodo di codice gestito <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> .  
  
 È facoltativo, ma consigliato, per consentire l'accesso a questa nuova pagina tramite il modello di automazione. Questa operazione può essere eseguita tramite i passaggi seguenti:  
  
1. Estendere l' <xref:EnvDTE._DTE.Properties%2A> oggetto tramite l'implementazione di un oggetto derivato da IDispatch.  
  
2. Restituisce un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Metodo (o per il codice gestito del <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metodo) all'oggetto derivato da IDispatch.  
  
3. Quando un consumer di automazione chiama il <xref:EnvDTE._DTE.Properties%2A> metodo in una pagina delle proprietà di un' **opzione** personalizzata, l'ambiente USA il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo per ottenere un'implementazione di automazione della pagina **Opzioni degli strumenti** personalizzata.  
  
4. L'oggetto di automazione del pacchetto VSPackage viene quindi usato per fornire ogni <xref:EnvDTE.Property> restituito da <xref:EnvDTE._DTE.Properties%2A> .  
  
   Per un esempio di implementazione di una pagina di opzioni degli strumenti personalizzata, vedere [esempi di VSSDK](../../misc/vssdk-samples.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)
