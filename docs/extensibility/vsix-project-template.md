---
title: Modello Project VSIX | Microsoft Docs
description: Informazioni su come usare il modello vsix Project per eseguire il wrapping delle estensioni Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto in Visual Studio Marketplace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6d6cb7112d404b0ecc9decbc7e5b7caea251ab35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109773"
---
# <a name="vsix-project-template"></a>Modello di progetto VSIX

È possibile usare il modello VSIX Project per eseguire il wrapping di una o più estensioni Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel sito Web [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 La distribuzione VSIX supporta VSPackage, assembly, componenti MEF, modelli di progetto, modelli di elemento, controlli della casella degli strumenti e tipi di estensione personalizzati.

> [!NOTE]
> Per usare i progetti VSIX, è necessario installare Visual Studio SDK. Per altre informazioni sull'SDK Visual Studio, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Posizione in cui trovare il modello di progetto VSIX

Il modello di Project VSIX è disponibile nella finestra **di dialogo Nuovo Project** cercando "vsix".  È presente sia una versione C# che Visual Basic versione.

> [!TIP]
> È necessario assicurarsi che .NET Framework 4.5 o versione successiva sia specificato nella casella di riepilogo a discesa nella parte superiore della finestra di **dialogo Nuovo** Project.

## <a name="uses-of-the-vsix-project-template"></a>Usi del modello di progetto VSIX

Il modello di progetto VSIX ha due usi principali:

- Per distribuire modelli di progetto, modelli di elemento ed estensioni.

- Per eseguire il wrapping degli output di più estensioni in un unico pacchetto di distribuzione.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Creazione del pacchetto di un'estensione in un progetto VSIX vuoto

È possibile creare un pacchetto di un'estensione esistente o un'estensione che non dispone già del supporto VSIX, tramite wrapping in un progetto VSIX vuoto. L'estensione di cui eseguire il wrapping deve essere di un tipo supportato dallo [schema VSIX.](../extensibility/vsix-extension-schema-2-0-reference.md)

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Per creare un pacchetto di un'estensione usando un progetto VSIX

1. Compilare i progetti che costituiscono l'estensione.

2. Creare un progetto VSIX usando il modello **di Project VSIX.**

    *Source.extension.vsixmanifest* viene aperto in **Progettazione manifesto**.

3. Nella **scheda Asset** scegliere il **pulsante** Nuovo.

    Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo asset.

4. **Nell'elenco Tipo** scegliere il tipo di estensione da aggiungere.

5. Per aggiungere un'estensione o un elemento di contenuto incluso nella soluzione corrente, ad esempio un modello di elemento o un assembly compilato, seguire questa procedura:

   1. **Nell'elenco Origine** scegliere **Un progetto nella soluzione corrente**.

   2. **Nell'Project** selezionare il nome dell'estensione.

   3. Nella casella **Incorpora in questa cartella** immettere il nome di una cartella in cui incorporare l'asset e quindi scegliere **OK.**

6. Per aggiungere un'estensione o un elemento di contenuto non incluso nella soluzione corrente, seguire questa procedura:

   1. Nella casella **di** riepilogo Origine scegliere **File nel file system**.

   2. Nel campo **Percorso** immettere il percorso completo del file di estensione compilato o compresso oppure usare il pulsante **Sfoglia** per passare al file.

   3. Nella casella **Incorpora in questa cartella** immettere il nome di una cartella in cui incorporare l'asset e quindi scegliere **OK.**

7. Se si vuole che il pacchetto includa estensioni aggiuntive, aggiungerle nello stesso modo.

8. Compilare la soluzione.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila un file *vsix* che contiene un file manifesto VSIX, un file *.xml* [Content_Types] e tutti gli asset di estensione aggiunti al progetto.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sullo schema dell'estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
