---
title: Panoramica del servizio di linguaggio legacy - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707351"
---
# <a name="legacy-language-service-overview"></a>Panoramica dei servizi di linguaggio legacy
Un servizio di linguaggio fornisce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il supporto dell'editor che consente di implementare determinate funzionalità. Le classi del servizio di linguaggio Managed Package Framework (MPF) forniscono supporto completo per le funzionalità utilizzate di frequente e il supporto parziale per altre funzionalità.

## <a name="fully-supported-features-in-the-mpf"></a>Funzionalità completamente supportate in MPF
 Le classi del servizio di linguaggio MPF supportano le funzionalità seguenti:The MPF language service classes support the following features:

- Evidenziazione della sintassi

- struttura

- Aggiunta di commenti a blocchi di codice

- Corrispondenza parentesi graffe

- Frammenti di codice

- Proprietà personalizzate del documento

- Informazioni sui parametri IntelliSense

- Informazioni rapide su IntelliSense

- Completamento dei membri IntelliSense

- Completamento delle parole IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Funzionalità parzialmente supportate in MPF
 Il MPF fornisce solo un supporto parziale per le seguenti funzionalità. Ciò significa che è necessario implementare i metodi chiamati da MPF.

- Riformattare il codice. Viene fornito il codice che implementa la riformattazione.

- Convalida dei punti di interruzione identificando intervalli di codice validi. Il codice che identifica gli intervalli di codice viene fornito.

- Supporto della finestra **Auto** del debugger per la visualizzazione delle variabili. Specificare il codice che determina cosa visualizzare nella finestra.

- Supporto della **barra di spostamento** per la navigazione rapida tra tipi e membri. Implementare e restituire una classe helper che popola gli elenchi nelle caselle combinate della barra di **spostamento.**

## <a name="implementation"></a>Implementazione
 È necessario completare diversi passaggi per implementare il servizio di linguaggio stesso e le funzionalità del servizio di linguaggio che si desidera supportare per la lingua. Questi passaggi vengono illustrati negli argomenti seguenti:These steps are discussed in the following topics:

- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Corrispondenza parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Struttura in un servizio di linguaggio legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Aggiunta di commenti al codice in un servizio di linguaggio legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Riformattazione del codice in un servizio di linguaggio legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Proprietà personalizzate dei documenti in un servizio di linguaggio legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Supporto per i frammenti di codice in un servizio di linguaggio legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Supporto per la barra di spostamento in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Completamento dei membri in un servizio di linguaggio legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Informazioni rapide in un servizio di linguaggio legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Supporto per la finestra Auto in un servizio di linguaggio legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Convalida dei punti di interruzione in un servizio di linguaggio legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Vedere anche
- [Implementazione di un servizio di linguaggio legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)
