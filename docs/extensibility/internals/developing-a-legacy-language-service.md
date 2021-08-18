---
title: Sviluppo di un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sull'implementazione di un servizio di linguaggio legacy come parte di un VSPackage o sull'uso di Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b300756334a84dd2e3d6ade83cc48caa10349bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124620"
---
# <a name="develop-a-legacy-language-service"></a>Sviluppare un servizio di linguaggio legacy
Questa sezione contiene collegamenti ad argomenti che consentono di creare un servizio di linguaggio legacy.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio di linguaggio.](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="in-this-section"></a>Contenuto della sezione
- [Modello di un servizio di linguaggio legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Fornisce un modello di un servizio di linguaggio minimo per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'editor principale. È possibile usare questo modello come guida per la creazione di un servizio di linguaggio personalizzato.

- [Interfacce del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-interfaces.md)

 Vengono illustrati gli oggetti necessari per implementare un servizio di linguaggio e viene fornito un elenco di oggetti aggiuntivi che è possibile usare per fornire l'evidenziazione della sintassi, i dati dei metodi e altre funzionalità.

- [Intercettare i comandi del servizio di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Viene descritto come inserire un filtro comandi nel servizio di linguaggio per intercettare i comandi che altrimenti verrebbero gestiti dalla visualizzazione testo.

- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Fornisce informazioni su come registrare il servizio di linguaggio tramite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Supporto del servizio di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md)

 Viene descritto in che modo un servizio di linguaggio può fornire funzionalità per supportare un debugger.

- [Elenco di controllo: Creare un servizio di linguaggio legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Fornisce istruzioni dettagliate per la creazione e l'integrazione di un servizio di linguaggio per l'editor principale.

## <a name="related-sections"></a>Sezioni correlate
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Viene illustrato come implementare l'evidenziazione della sintassi nel servizio di linguaggio.

- [Completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Viene illustrato il completamento delle istruzioni, il processo tramite il quale un servizio di linguaggio consente agli utenti di completare una parola chiave o un elemento del linguaggio che hanno iniziato a digitare.

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Viene descritto come fornire suggerimenti sui metodi per le funzioni e i metodi di overload.

- [Procedura: Fornire supporto per il testo nascosto in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Viene illustrato lo scopo di un'area di testo nascosto e vengono fornite istruzioni su come implementare un'area di testo nascosto.

- [Procedura: Fornire supporto della struttura espansa in un servizio di linguaggio legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Vengono illustrate le due opzioni che estendono il supporto della struttura per il linguaggio oltre al supporto del *comando Comprimi in* definizioni.
