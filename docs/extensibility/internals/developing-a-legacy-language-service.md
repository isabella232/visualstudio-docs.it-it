---
title: Sviluppo di un servizio di linguaggio Legacy Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708664"
---
# <a name="develop-a-legacy-language-service"></a>Sviluppare un servizio di linguaggio legacyDevelop a legacy language service
In questa sezione vengono forniti collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere Editor e estensioni del [servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Fornisce un modello di un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servizio di linguaggio minimo per l'editor principale. È possibile utilizzare questo modello come guida per la creazione di un servizio di linguaggio personalizzato.

- [Interfacce del servizio di linguaggio legacyLegacy language service interfaces](../../extensibility/internals/legacy-language-service-interfaces.md)

 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e viene fornito un elenco di oggetti aggiuntivi che è possibile utilizzare per fornire l'evidenziazione della sintassi, i dati del metodo e altre funzionalità.

- [Intercettare i comandi del servizio di linguaggio legacyIntercept legacy language service commands](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Viene descritto come inserire un filtro di comando nel servizio di linguaggio per intercettare i comandi che la visualizzazione di testo sarebbe altrimenti gestire.

- [Registrare un servizio di linguaggio legacyRegister a legacy language service](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Vengono fornite informazioni su come registrare il servizio di linguaggio utilizzando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Supporto del servizio di linguaggio per il debugLanguage service support for debugging](../../extensibility/internals/language-service-support-for-debugging.md)

 Viene descritto come un servizio di linguaggio può fornire funzionalità per supportare un debugger.

- [Elenco di controllo: creare un servizio di linguaggio legacyChecklist: Create a legacy language service](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Vengono fornite istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor principale.

## <a name="related-sections"></a>Sezioni correlate
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'evidenziazione della sintassi nel servizio di linguaggio.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato il completamento delle istruzioni, il processo mediante il quale un servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento che hanno iniziato a digitare.

- [Informazioni sui parametri in un servizio di linguaggio legacyParameter Info in a legacy language service](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene descritto come fornire suggerimenti sui metodi per le funzioni e i metodi in overload.

- [Procedura: fornire supporto per testo nascosto in un servizio di linguaggio legacyHow to: Provide hidden text support in a legacy language service](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Viene illustrato lo scopo di un'area di testo nascosto e vengono fornite istruzioni su come implementare un'area di testo nascosto.

- [Procedura: fornire il supporto della struttura espansa in un servizio di linguaggio legacyHow to: Provide expanded outlining support in a legacy language service](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrate le due opzioni che estendono il supporto della struttura per il linguaggio oltre al supporto del comando *Comprimi alle definizioni.*
