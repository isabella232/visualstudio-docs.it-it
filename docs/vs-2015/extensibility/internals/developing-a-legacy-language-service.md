---
title: Sviluppo di un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839695"
---
# <a name="developing-a-legacy-language-service"></a>Sviluppo di un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa sezione contiene collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornisce un modello di un servizio di linguaggio minimo per l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principale di. È possibile utilizzare questo modello come guida per la creazione di un servizio di linguaggio personalizzato.  
  
 [Interfacce dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e viene fornito un elenco di oggetti aggiuntivi che è possibile utilizzare per fornire l'evidenziazione della sintassi, i dati del metodo e altre funzionalità.  
  
 [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Viene descritto come inserire un filtro dei comandi nel servizio di linguaggio per intercettare i comandi che la visualizzazione di testo altrimenti gestirebbe.  
  
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Vengono fornite informazioni su come registrare il servizio di linguaggio utilizzando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.  
  
 [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor principale di.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Viene illustrato come implementare l'evidenziazione della sintassi nel servizio di linguaggio.  
  
 [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Viene illustrato il completamento delle istruzioni, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave o un elemento del linguaggio che hanno iniziato a digitare.  
  
 [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Viene descritto come fornire suggerimenti per metodi e funzioni in overload.  
  
 [Procedura: Fornire il supporto per il testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Viene illustrato lo scopo di un'area di testo nascosta e vengono fornite istruzioni su come implementare un'area di testo nascosta.  
  
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Vengono illustrate le due opzioni che estendono il supporto della struttura per il linguaggio oltre al supporto del comando *Comprimi a definizioni* .
