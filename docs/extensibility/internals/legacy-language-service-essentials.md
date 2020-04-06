---
title: Informazioni di base sul servizio di linguaggio Legacy Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707415"
---
# <a name="legacy-language-service-essentials"></a>Nozioni fondamentali sui servizi di linguaggio legacy
È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio.You must provide a language service to integrate a programming language into Visual Studio. In questo argomento vengono illustrate le funzionalità disponibili nei servizi di linguaggio legacy.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare un servizio di linguaggio, vedere [Editor e estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

 I servizi di linguaggio legacy offrono le funzionalità seguenti:Legacy language services provide the following features:

|Funzionalità|Descrizione|
|-------------|-----------------|
|Colorazione della sintassi|Determina la visualizzazione dell'editor per visualizzare diversi colori e stili di carattere per i diversi elementi di una lingua. Questa differenziazione può semplificare la lettura e la modifica dei file.<br /><br /> Per informazioni generali, vedere [Colorazione della sintassi in un servizio](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)di linguaggio Legacy .<br /><br /> Per informazioni su questa funzionalità nel framework del pacchetto gestito (MPF), vedere [Colorazione della sintassi in un](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)servizio di linguaggio Legacy .|
|Completamento istruzioni|Completa un'istruzione o una parola chiave che l'utente ha iniziato a digitare. Il completamento delle istruzioni consente agli utenti di inserire istruzioni difficili più facilmente, con meno digitazione e meno possibilità di errore.<br /><br /> Per informazioni generali, vedere [Completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità di MPF, vedere [Completamento di parole in un servizio](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)di linguaggio Legacy .|
|Corrispondenza parentesi graffe|Evidenzia i caratteri accoppiati, ad esempio le parentesi graffe. Quando l'utente digita un carattere di chiusura, ad esempio """, la corrispondenza tra parentesi graffe evidenzia il carattere di apertura corrispondente, ad esempio "".</a0> Quando sono presenti diversi livelli di caratteri di inclusione, questa funzionalità consente agli utenti di verificare che i caratteri di inclusione siano associati correttamente.<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [Corrispondenza tra parentesi graffe in un](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)servizio di linguaggio Legacy .|
|Descrizioni comandi per le informazioni sui parametri|Visualizza un elenco di firme possibili per il metodo di overload che l'utente sta digitando.<br /><br /> Per informazioni generali, vedere Informazioni sui parametri in un servizio di [linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Per informazioni su questa funzionalità di MPF, vedere Informazioni sui parametri [in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marcatori di errore|Visualizza una sottolineatura rossa ondulata, nota anche come ondulata, sotto un testo sintatticamente errato. Gli indicatori di errore vengono in genere utilizzati per invitare gli utenti a conoscere parole chiave errate, parentesi non chiuse, caratteri non validi ed errori simili.<br /><br /> Nelle classi MPF, gli indicatori di errore <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> vengono <xref:Microsoft.VisualStudio.Package.AuthoringSink> gestiti automaticamente nel metodo della classe.|

 Molte di queste funzionalità richiedono il servizio di linguaggio per analizzare il codice sorgente. Spesso è possibile riutilizzare il codice di tokenizzazione e analisi per il compilatore o l'interprete.

 Le funzionalità seguenti sono correlate al supporto per i linguaggi di programmazione, ma non fanno parte dei servizi di linguaggio:

| Funzionalità | Descrizione |
|-----------------------| - |
| Valutatori di espressioni | Supporta il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger convalidando i punti di interruzione e fornendo un elenco di espressioni da visualizzare nella finestra di debug **auto.**<br /><br /> Per ulteriori informazioni, vedere Supporto del servizio di [linguaggio per il debug](../../extensibility/internals/language-service-support-for-debugging.md). |
| Strumenti di esplorazione dei simboli | Supporta **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate**e Trova risultati **simbolo**. |
