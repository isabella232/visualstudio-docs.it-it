---
title: EditorConfig rispetto agli analizzatori
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301692"
---
# <a name="code-analysis-faq"></a>Domande frequenti sull'analisi del codice

Questa pagina contiene le risposte ad alcune domande frequenti sull'analisi del codice basata su piattaforma del compilatore .NET in Visual Studio.This page contains answers to some frequently asked questions about .NET Compiler Platform-based code analysis in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Analisi del codice e EditorConfigCode analysis versus EditorConfig

**D:** È necessario utilizzare l'analisi del codice o EditorConfig per il controllo dello stile del codice?

**R:** L'analisi del codice e i file EditorConfig funzionano in mano. Quando si definiscono gli stili di codice [in un file EditorConfig](../ide/editorconfig-code-style-settings-reference.md) o nella pagina Opzioni dell'editor di [testo,](../ide/code-styles-and-code-cleanup.md) si stanno effettivamente configurando gli analizzatori di codice incorporati in Visual Studio. I file EditorConfig possono essere utilizzati per abilitare o disabilitare le regole dell'analizzatore e anche per configurare alcuni pacchetti dell'analizzatore NuGet, ad esempio [gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig e set di regole

**D:** È necessario configurare gli analizzatori utilizzando un set di regole o un file EditorConfig?

**R**: I set di regole e i file EditorConfig possono coesistere ed entrambi per configurare gli analizzatori. Sia i file EditorConfig che i set di regole consentono di abilitare e disabilitare le regole e di impostarne la gravità.

Tuttavia, i file EditorConfig offrono altri modi per configurare le regole troppo:

- Per gli analizzatori FxCop, i file EditorConfig consentono di [definire i tipi di codice da analizzare.](fxcop-analyzer-options.md)
- Per gli analizzatori di stile di codice incorporati in Visual Studio, i file EditorConfig consentono di [definire gli stili](../ide/editorconfig-code-style-settings-reference.md) di codice preferiti per una codebase.

Oltre ai set di regole e ai file EditorConfig, alcuni analizzatori vengono configurati tramite l'utilizzo di file di testo contrassegnati come [file aggiuntivi](../ide/build-actions.md#build-action-values) per i compilatori di C e VB.

> [!NOTE]
> - I file EditorConfig possono essere usati solo per abilitare le regole e impostarne la gravità in Visual Studio 2019 versione 16.3 e successive.
> - I file EditorConfig non possono essere utilizzati per configurare l'analisi legacy, mentre i set di regole possono.

## <a name="code-analysis-in-ci-builds"></a>Analisi del codice nelle compilazioni CICode analysis in CI builds

**D:** L'analisi del codice basata su piattaforma del compilatore .NET funziona nelle compilazioni di integrazione continua (CI)?

**R:** Sì. Per gli analizzatori installati da un pacchetto NuGet, tali regole vengono [applicate in fase di compilazione,](roslyn-analyzers-overview.md#build-errors)anche durante una compilazione CI. Gli analizzatori utilizzati nelle compilazioni CI rispettano la configurazione delle regole sia dai set di regole che dai file EditorConfig. Attualmente, gli analizzatori di codice incorporati in Visual Studio non sono disponibili come pacchetto NuGet e pertanto queste regole non sono applicabili in una compilazione CI.

## <a name="ide-analyzers-versus-stylecop"></a>Analizzatori IDE e StyleCop

**D:** Qual è la differenza tra gli analizzatori di codice IDE di Visual Studio e gli analizzatori StyleCop?

**R:** l'IDE di Visual Studio include analizzatori incorporati che cercano sia lo stile del codice che i problemi di qualità. Queste regole consentono di utilizzare le nuove funzionalità del linguaggio man mano che vengono introdotte e di migliorare la manutenibilità del codice. Analizzatori IDE vengono continuamente aggiornati con ogni versione di Visual Studio.IDE analyzers are continually updated with each Visual Studio release.

[Gli analizzatori StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sono analizzatori di terze parti installati come pacchetto NuGet che verificano la coerenza dello stile nel codice. In generale, le regole StyleCop consentono di impostare le preferenze personali per una base di codice senza consigliare uno stile rispetto a un altro.

## <a name="code-analyzers-versus-legacy-analysis"></a>Analizzatori di codice e analisi legacyCode analyzers versus legacy analysis

**D:** Qual è la differenza tra l'analisi legacy e l'analisi del codice basata su piattaforma del compilatore .NET?

**R:** L'analisi del codice basata su piattaforma del compilatore .NET analizza il codice sorgente in tempo reale e durante la compilazione, mentre l'analisi legacy analizza i file binari al termine della compilazione. Per ulteriori informazioni, vedere [Analisi basata su piattaforma del compilatore .NET rispetto all'analisi legacy](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) e [Domande frequenti sugli analizzatori FxCop](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Considera gli avvisi come errori

**D:** Il progetto utilizza l'opzione di compilazione per considerare gli avvisi come errori. Dopo la migrazione dall'analisi legacy all'analisi del codice sorgente, tutti gli avvisi dell'analisi del codice vengono ora visualizzati come errori. Come posso impedirlo?

**R**: Per evitare che gli avvisi dell'analisi del codice vengano considerati come errori, attenersi alla seguente procedura:

  1. Creare un file .props con il seguente contenuto:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Aggiungere una riga al file di progetto con estensione csproj o vbproj per importare il file con estensione props creato nel passaggio precedente. Questa riga deve essere posizionata prima di tutte le righe che importano i file .props dell'analizzatore FxCop. Ad esempio, se il file props è denominato codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>Vedere anche

- [Panoramica degli analizzatori](roslyn-analyzers-overview.md)
- [Impostazioni della convenzione di codifica .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
