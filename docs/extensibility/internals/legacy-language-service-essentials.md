---
title: Servizi di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707415"
---
# <a name="legacy-language-service-essentials"></a>Nozioni fondamentali sui servizi di linguaggio legacy
È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio. In questo argomento vengono illustrate le funzionalità disponibili nei servizi di linguaggio legacy.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

 I servizi di linguaggio legacy forniscono le funzionalità seguenti:

|Feature|Descrizione|
|-------------|-----------------|
|Colorazione della sintassi|Consente alla visualizzazione dell'editor di visualizzare colori e stili dei tipi di carattere diversi per i diversi elementi di una lingua. Questa differenziazione può semplificare la lettura e la modifica dei file.<br /><br /> Per informazioni generali, vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità nel Framework di pacchetto gestito (MPF), vedere [colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Completamento istruzioni|Completa un'istruzione o una parola chiave che l'utente ha iniziato a digitare. Il completamento delle istruzioni consente agli utenti di immettere più facilmente istruzioni complesse, con minore digitazione e meno probabilità di errore.<br /><br /> Per informazioni generali, vedere [completamento delle istruzioni in un servizio di linguaggio legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [completamento delle parole in un servizio di linguaggio legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Corrispondenza parentesi graffe|Evidenzia i caratteri abbinati, ad esempio le parentesi graffe. Quando l'utente digita un carattere di chiusura come "}", la corrispondenza tra parentesi graffe evidenzia il carattere di apertura corrispondente, ad esempio "{". Quando sono presenti diversi livelli di caratteri di inclusione, questa funzionalità consente agli utenti di verificare che i caratteri di inclusione siano abbinati correttamente.<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [corrispondenza tra parentesi graffe in un servizio di linguaggio legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Descrizioni comandi delle informazioni sui parametri|Visualizza un elenco di possibili firme per il metodo di overload attualmente digitato dall'utente.<br /><br /> Per informazioni generali, vedere [informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [informazioni sui parametri in un servizio di linguaggio legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marcatori di errore|Visualizza una sottolineatura rossa ondulata, nota anche come ondulata, sotto forma di testo sintatticamente non corretta. I marcatori di errore vengono in genere utilizzati per consentire agli utenti di riconoscere parole chiave errate, parentesi non chiuse, caratteri non validi ed errori simili.<br /><br /> Nelle classi MPF, i marcatori di errore vengono gestiti automaticamente nel <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo della <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|

 Molte di queste funzionalità richiedono che il servizio di linguaggio analizzi il codice sorgente. Spesso è possibile riutilizzare suddivisione in token e il codice di analisi per il compilatore o l'interprete.

 Le funzionalità seguenti sono correlate al supporto per i linguaggi di programmazione, ma non fanno parte dei servizi di linguaggio:

| Feature | Descrizione |
|-----------------------| - |
| Analizzatori di espressioni | Supporta il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger convalidando i punti di interruzione e fornendo un elenco di espressioni da visualizzare nella finestra di debug **auto** .<br /><br /> Per ulteriori informazioni, vedere [supporto del servizio di linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md). |
| Strumenti per l'esplorazione di simboli | Supporta i risultati di **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate**e **Trova simbolo**. |
