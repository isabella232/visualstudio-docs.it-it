---
title: Modello di progetto VSIX - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697928"
---
# <a name="vsix-project-template"></a>Modello di progetto VSIX

È possibile utilizzare il modello di progetto VSIX per eseguire il wrapping di una o più estensioni di Visual Studio in un progetto VSIX e quindi pubblicare il pacchetto nel sito Web di [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 La distribuzione VSIX supporta VSPackage, assembly, componenti MEF, modelli di progetto, modelli di elemento, controlli della casella degli strumenti e tipi di estensione personalizzati.

> [!NOTE]
> Per usare i progetti VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni su Visual Studio SDK, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Dove trovare il modello di progetto VSIX

Il modello di progetto VSIX è disponibile nella finestra di dialogo **Nuovo progetto** cercando "vsix".  È disponibile sia una versione di C, sia in Visual Basic.

> [!TIP]
> È necessario assicurarsi che .NET Framework 4.5 o versione successiva sia specificato nella casella di riepilogo a discesa nella parte superiore della finestra di dialogo **Nuovo progetto.**

## <a name="uses-of-the-vsix-project-template"></a>Utilizzi del modello di progetto VSIX

Il modello di progetto VSIX ha due usi principali:

- Per distribuire modelli di progetto, modelli di elemento ed estensioni.

- Per eseguire il wrapping degli output di più estensioni in un unico pacchetto di distribuzione.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Creazione del pacchetto di un'estensione in un progetto VSIX vuotoPackaging an extension in an empty VSIX project

È possibile creare un pacchetto di un'estensione esistente o di un'estensione che non dispone già del supporto VSIX, eseguendone il wrapping in un progetto VSIX vuoto. L'estensione di cui eseguire il wrapping deve essere di un tipo supportato dallo [schema VSIX.](../extensibility/vsix-extension-schema-2-0-reference.md)

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Per creare un pacchetto di un'estensione tramite un progetto VSIXTo package an extension by using a VSIX project

1. Compilare i progetti che costituiscono l'estensione.

2. Creare un progetto VSIX utilizzando il modello di **progetto VSIX.**

    *Source.extension.vsixmanifest verrà* aperto in **Progettazione manifesto**.

3. Nella scheda **Asset** scegliere il pulsante **Nuovo.**

    Viene visualizzata la finestra di dialogo **Aggiungi nuovo asset.**

4. Nell'elenco **Tipo** scegliere il tipo di estensione da aggiungere.

5. Per aggiungere un'estensione o un elemento di contenuto incluso nella soluzione corrente (ad esempio, un modello di elemento o un assembly compilato), eseguire la procedura seguente:To add an extension or content element that's included in the current solution (for example, an item template or a compiled assembly), perform the following steps:

   1. Nell'elenco **Origine** scegliere **Un progetto nella soluzione corrente.**

   2. Nell'elenco **Progetto** scegliere il nome dell'estensione.

   3. Nella casella **Incorpora in questa cartella** immettere il nome di una cartella in cui incorporare la risorsa, quindi scegliere OK. **OK**

6. Per aggiungere un'estensione o un elemento di contenuto non incluso nella soluzione corrente, eseguire la procedura seguente:To add an extension or content element that isn't included in the current solution, perform the following steps:

   1. Nella casella **di** riepilogo Origine scegliere **File nel file system**.

   2. Nel campo **Percorso** immettere il percorso completo del file di estensione compilato o compresso oppure utilizzare il pulsante **Sfoglia** per individuare il file.

   3. Nella casella **Incorpora in questa cartella** immettere il nome di una cartella in cui incorporare la risorsa, quindi scegliere OK. **OK**

7. Se vuoi che il pacchetto includa estensioni aggiuntive, aggiungile nello stesso modo.

8. Compilare la soluzione.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compila un file *VSIX* contenente un file manifesto VSIX, un file*XML* [Content_Types] e tutti gli asset di estensione aggiunti al progetto.

## <a name="see-also"></a>Vedere anche

- [Riferimento allo schema di estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
