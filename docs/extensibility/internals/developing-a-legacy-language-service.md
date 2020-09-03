---
title: Sviluppo di un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708664"
---
# <a name="develop-a-legacy-language-service"></a>Sviluppare un servizio di linguaggio legacy
Questa sezione contiene collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Fornisce un modello di un servizio di linguaggio minimo per l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor principale di. È possibile utilizzare questo modello come guida per la creazione di un servizio di linguaggio personalizzato.

- [Interfacce del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)

 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e viene fornito un elenco di oggetti aggiuntivi che è possibile utilizzare per fornire l'evidenziazione della sintassi, i dati del metodo e altre funzionalità.

- [Intercettare i comandi del servizio di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Viene descritto come inserire un filtro dei comandi nel servizio di linguaggio per intercettare i comandi che la visualizzazione di testo altrimenti gestirebbe.

- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Vengono fornite informazioni su come registrare il servizio di linguaggio utilizzando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Supporto del servizio di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)

 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.

- [Elenco di controllo: creare un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor principale di.

## <a name="related-sections"></a>Sezioni correlate
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'evidenziazione della sintassi nel servizio di linguaggio.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato il completamento delle istruzioni, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave o un elemento del linguaggio che hanno iniziato a digitare.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene descritto come fornire suggerimenti per metodi e funzioni in overload.

- [Procedura: fornire il supporto per testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Viene illustrato lo scopo di un'area di testo nascosta e vengono fornite istruzioni su come implementare un'area di testo nascosta.

- [Procedura: fornire il supporto per la struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrate le due opzioni che estendono il supporto della struttura per il linguaggio oltre al supporto del comando *Comprimi a definizioni* .
