---
title: Nozioni fondamentali sui servizi di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a3926ff84f3b2e6415df1ca7333409c05d839685
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436270"
---
# <a name="legacy-language-service-essentials"></a>Nozioni fondamentali sui servizi di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È necessario fornire un servizio di linguaggio per integrare un linguaggio di programmazione in Visual Studio. In questo argomento illustra le funzionalità disponibili in servizi di linguaggio legacy.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Servizi di linguaggio legacy forniscono le funzionalità seguenti:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Colorazione della sintassi|Fa sì che la visualizzazione dell'editor visualizzare diversi colori e stili di carattere per gli elementi di una lingua diversi. Questa distinzione può rendere più facile da leggere e modificare i file.<br /><br /> Per informazioni generali, vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità nel framework di pacchetto gestito (MPF), vedere [colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Completamento istruzioni|Completa un'istruzione o parola chiave che l'utente ha avviato la digitazione. Completamento istruzioni consente agli utenti di immettere istruzioni difficile più facilmente con più rapido e meno probabilità di errore.<br /><br /> Per informazioni generali, vedere [completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [completamento delle parole in un servizio di linguaggio Legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Corrispondenza parentesi graffe|Evidenziazioni abbinate caratteri, ad esempio le parentesi graffe. Quando l'utente digita un carattere di chiusura, ad esempio "}", corrispondenza parentesi graffe vengono evidenziate corrispondente carattere, di apertura, ad esempio "{". Quando sono presenti diversi livelli di caratteri di inclusione, questa funzionalità consente agli utenti di confermare che i caratteri che lo contiene sono abbinati correttamente.<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [corrispondenza delle parentesi graffe in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Descrizioni comandi informazioni parametro|Visualizza un elenco di firme possibili per il metodo di overload che l'utente attualmente sta digitando.<br /><br /> Per informazioni generali, vedere [informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Per informazioni su questa funzionalità in MPF, vedere [informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Indicatori di errore|Visualizza una sottolineatura rossa ondulata, noto anche come un ondulata, sotto il testo che è sintatticamente corretto. Gli indicatori di errore vengono in genere usati per informare gli utenti delle parole chiave con errori di ortografia, le parentesi non chiusa, caratteri non validi ed errori simili.<br /><br /> Nelle classi di MPF, gli indicatori di errore vengono gestiti automaticamente nel <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metodo di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|  
  
 Molte di queste funzionalità richiedono il servizio di linguaggio per analizzare il codice sorgente. È spesso possibile riutilizzare la suddivisione in token e l'analisi del codice per il compilatore o l'interprete.  
  
 Le funzionalità seguenti sono correlate al supporto per linguaggi di programmazione, ma non fanno parte di servizi di linguaggio:  
  
|Funzionalità|Descrizione|  
|-------------|-----------------|  
|Analizzatori di espressioni|Supporta il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger convalidando i punti di interruzione e specificando un elenco di espressioni da visualizzare nella **Auto** finestra di debug.<br /><br /> Per altre informazioni, vedere [supporto per il debug del servizio linguaggio](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Strumenti di esplorazione dei simboli|Supporta **Visualizzatore oggetti**, **Visualizzazione classi**, **Visualizzatore chiamate**, e **risultati ricerca simbolo**.|
