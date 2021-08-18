---
title: Strumenti di localizzazione
description: Informazioni sugli strumenti di localizzazione inclusi in Visual Studio e su come usarli per creare applicazioni localizzate in più lingue.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4411ab1280bc8c39fcbf49a5ee80f1722a84d1d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086157"
---
# <a name="develop-globalized-and-localized-apps"></a>Sviluppare app globalizzate e localizzate

Visual Studio semplifica lo sviluppo di applicazioni internazionali grazie alla possibilità di sfruttare i servizi incorporati in [.NET](/dotnet/standard/globalization-localization/).

Ad esempio, il sistema di progetto per app Windows Forms può generare file di risorse per le impostazioni cultura dell'interfaccia utente di fallback e ogni assembly di impostazioni cultura dell'interfaccia utente aggiuntivo. Quando si compila un progetto in Visual Studio, i file di risorse vengono compilati dal formato XML di Visual Studio (con estensione resx) in un formato binario intermedio (con estensione resources) e quindi incorporati in assembly satellite. Per altre informazioni, vedere [File di risorse in Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) e [Creare assembly satellite per applicazioni desktop](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Lingue bidirezionali

È possibile usare Visual Studio per creare applicazioni che visualizzano correttamente il testo nelle lingue scritte da destra a sinistra, tra cui l'arabo e l'ebraico. Per alcune funzionalità basta impostare delle proprietà. In altri casi è necessario implementare le funzionalità nel codice.

> [!NOTE]
> Per l'immissione e la visualizzazione delle lingue bidirezionali è necessario usare una versione di Windows configurata per la lingua appropriata. Può essere una versione di Windows in inglese con il Language Pack appropriato o una versione di Windows localizzata nella lingua desiderata.

### <a name="apps-that-support-bidirectional-languages"></a>App con supporto per le lingue bidirezionali

- App di Windows

   È possibile creare applicazioni completamente bidirezionali che includono il supporto per il testo bidirezionale, l'ordine di lettura da destra a sinistra e il mirroring (inversione del layout di finestre, menu, finestre di dialogo e così via). Fatta eccezione per il mirroring, queste funzionalità sono disponibili per impostazione predefinita o come impostazioni di proprietà. Il mirroring è supportato intrinsecamente per alcune funzionalità, ad esempio le finestre di messaggio. In altri casi è invece necessario implementare il mirroring nel codice. Per altre informazioni, vedere [Supporto bidirezionale per Windows applicazioni Form.](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)

- App Web

   I servizi Web supportano l'invio e la ricezione di testo UTF-8 e Unicode. Sono quindi adatti per le applicazioni che prevedono l'uso delle lingue bidirezionali. L'interfaccia utente delle applicazioni Web client è basata sui browser, pertanto il livello di supporto bidirezionale di un'applicazione Web dipende dal grado di supporto delle funzionalità bidirezionali nel browser dell'utente. In Visual Studio è possibile creare applicazioni con supporto per testo in arabo o ebraico, ordine di lettura da destra a sinistra, codifica di file e impostazioni cultura locali. Per altre informazioni, vedere [Supporto bidirezionale per ASP.NET applicazioni Web.](/previous-versions/6eedwbtt(v=vs.140))

> [!NOTE]
> Le app console non includono il supporto del testo per le lingue bidirezionali. Questo fatto dipende dall'interazione tra Windows e le applicazioni console.

## <a name="see-also"></a>Vedi anche

- [Supporto per le lingue bidirezionali in Visual Studio](use-bidirectional-languages.md)
- [Globalizzare e localizzare app .NET](/dotnet/standard/globalization-localization/)
- [Risorse nelle app .NET](/dotnet/framework/resources/)