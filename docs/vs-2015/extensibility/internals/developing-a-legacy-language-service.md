---
title: Sviluppo di un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c77ec89cb7c9e2b62bc31dce0763ea5fac419e23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525901"
---
# <a name="developing-a-legacy-language-service"></a>Sviluppo di un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [lo sviluppo di un servizio di linguaggio Legacy](https://docs.microsoft.com/visualstudio/extensibility/internals/developing-a-legacy-language-service).  
  
Questa sezione sono riportati i collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Fornisce un modello di un servizio di linguaggio minimo per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principale. È possibile usare questo modello come guida per la creazione di un proprio servizio di linguaggio.  
  
 [Interfacce dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Descrive gli oggetti necessari per implementare un servizio di linguaggio e fornisce un elenco di oggetti aggiuntivi che è possibile usare per fornire l'evidenziazione della sintassi, i dati del metodo e altre funzionalità.  
  
 [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Viene descritto come inserire un filtro di comando nel servizio di linguaggio per intercettare i comandi che in caso contrario, è necessario gestire la visualizzazione di testo.  
  
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Fornisce informazioni su come registrare il servizio di linguaggio usando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Supporto dei servizi di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)  
 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.  
  
 [Elenco di controllo: Creazione di un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor principale.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Viene illustrato come implementare l'evidenziazione della sintassi nel servizio di linguaggio.  
  
 [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Illustra il completamento, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o l'elemento che è stato avviato digitando.  
  
 [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Viene descritto come fornire suggerimenti di metodo per le funzioni in overload e i metodi.  
  
 [Procedura: Fornire il supporto per il testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Viene illustrato lo scopo di un'area di testo nascosto e vengono fornite istruzioni su come implementare un'area di testo nascosto.  
  
 [Procedura: Fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Illustra le due opzioni che estendono il supporto della struttura per il linguaggio oltre, supportando il *Comprimi alle definizioni* comando.

